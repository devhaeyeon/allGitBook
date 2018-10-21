# \[도커\] docker compose를 활용한 엔진엑스+몽고db+익스프레스 환경 셋팅1



![](http://cfile5.uf.tistory.com/image/9915F8365AB0BA8B302890)

docker가 무엇인지, docker compose가 무엇인지 

대략적으로 앞서 다뤘으니,

이젠 실전으로 !!

docker compose를 활용하여 엔진엑스 + 몽고db + 익스프레스 환경을 셋팅하려고 합니다. 

docker에서 엔진엑스, 몽고db는 도커 허브에서 제공 하고 있으니 해당 사이트를 이용합니다. 

docker compose버젼은 3으로 진행합니다. 

https://docs.docker.com/compose/compose-file/

**실전에 들어가기 전에 ...**

```text
version: "3"
services:

  redis:
    image: redis:alpine
    ports:
      - "6379"
    networks:
      - frontend
    deploy:
      replicas: 2
      update_config:
        parallelism: 2
        delay: 10s
      restart_policy:
        condition: on-failure

  db:
    image: postgres:9.4
    volumes:
      - db-data:/var/lib/postgresql/data
    networks:
      - backend
    deploy:
      placement:
        constraints: [node.role == manager]

  vote:
    image: dockersamples/examplevotingapp_vote:before
    ports:
      - 5000:80
    networks:
      - frontend
    depends_on:
      - redis
    deploy:
      replicas: 2
      update_config:
        parallelism: 2
      restart_policy:
        condition: on-failure

  result:
    image: dockersamples/examplevotingapp_result:before
    ports:
      - 5001:80
    networks:
      - backend
    depends_on:
      - db
    deploy:
      replicas: 1
      update_config:
        parallelism: 2
        delay: 10s
      restart_policy:
        condition: on-failure

  worker:
    image: dockersamples/examplevotingapp_worker
    networks:
      - frontend
      - backend
    deploy:
      mode: replicated
      replicas: 1
      labels: [APP=VOTING]
      restart_policy:
        condition: on-failure
        delay: 10s
        max_attempts: 3
        window: 120s
      placement:
        constraints: [node.role == manager]

  visualizer:
    image: dockersamples/visualizer:stable
    ports:
      - "8080:8080"
    stop_grace_period: 1m30s
    volumes:
      - "/var/run/docker.sock:/var/run/docker.sock"
    deploy:
      placement:
        constraints: [node.role == manager]

networks:
  frontend:
  backend:

volumes:
  db-data:
```

위의 코드는 compose file version 3의 예시 입니다. 

&lt;key&gt;:&lt;option&gt;:&lt;value&gt;의 구조로 Compose 파일이 구성이 됩니다. 

멀티 컨테이너 앱, 서비스 정의 및 스웜모드를 구현을 위한 version3 Compose는시작 튜토리얼을 통해 익힙니다.

- [docker-compose.yml](https://docs.docker.com/get-started/part3/#your-first-docker-composeyml-file) 을 만듦.

- [새로운 서비스 추가 및 재 배포](https://docs.docker.com/get-started/part5/#add-a-new-service-and-redeploy)

Composefile은 [services](https://docs.docker.com/compose/compose-file/#service-configuration-reference), [networks](https://docs.docker.com/compose/compose-file/#network-configuration-reference) 그리고 [volumes](https://docs.docker.com/compose/compose-file/#volume-configuration-reference)를 정의하고 있는[ YAML](http://yaml.org/)파일입니다.

시작! 

![](http://cfile8.uf.tistory.com/image/994AB0435AB1CC1A21BABE)

해당 구조를 가지고 프로젝트를 진행해보려고 합니다. 

step1. 작업 폴더를 만듦니다.  


step2.docker-compose.yml 파일을 만듧니다. 

step3. 해당 파일을 서비스에 맞게 작성합니다. 

.. 여기서 막힌 이슈 ,

&lt;key&gt;:&lt;option&gt;:&lt;value&gt;의 구조로 Compose 파일이 구성이 된다고 하였는데,

service, networks, volumes라는 것이 key일지, option에 해당할지 .. 

아니면 계층 구조를 가지는 건지 ... 

&gt;&gt;&gt;1depth , 2depth, 3depth .. 처럼 계층을 가진 형태의 depth를 가짐.

service에 대한 도큐먼트는

https://docs.docker.com/get-started/part3/\#about-services 에서 알 수 있다.

service의 값은 자신이 실행할 서비스명을 기입하면 됩니다.

