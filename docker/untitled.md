# \[도커\] Docker Compose란?

해당 글의 출처는

https://docs.docker.com/compose/에서 번역 및 의역을 한 것입니다.

compose file의 레퍼런스는 https://docs.docker.com/compose/compose-file/ 에서 찾을 수 있습니다.

**Compose란 ? \(툴이다!!!\)**

복수 개의 컨테이너를 실행시키는 도커 애플리케이션이 정의를 하기 위한 **툴**입니다.

Compose를 사용하면 YAML 파일을 사용하여 애플리케이션의 서비스를 구성할 수 있습니다.

그런 다음 single command를 사용하여 구성에서 모든 서비스를 만들고 시작합니다.

 Compose는 모든 환경\(workflow에서 production, staging, development, testing 및 CI 워크플로우\)을 포함합니다.

이 글을 통해 각각의 공통 사례들을 알 수 있습니다.

기본적으로 3스텝의 프로세스를 사용합니다.

1. 앱의 환경을 정의하여 어디에서나 재사용할 수 있는 Dockerfile을 정의합니다.

2. docker-compose.yml 에서 앱을 구성할 수 있는 서비스를 정의합니다. 그래서 단 하나의 환경ㅇ서 실행할 수 있게 합니다.

3. docker-compose up 명령어를 실행합니다. 그리고 Compose를 시작시키고 전체의 앱을 실행시킵니다.

샘플 docker-compose.yml은 아래와 같습니다.

```text
version: '3'
services:
  web:
    build: .
    ports:
    - "5000:5000"
    volumes:
    - .:/code
    - logvolume01:/var/log
    links:
    - redis
  redis:
    image: redis
volumes:
  logvolume01: {}
```

훨 씬 더 많은 정보는 https://docs.docker.com/compose/compose-file/ 에 있습니다.

Compose는 애플리케이션에서 아래의 라이프 사이클을 관리하기 위한 명령어를 가집니다.

- Start, stop, 그리고 rebuild service들

- 실행중인 서비스 상태를 보는 것.

- 실행중인 서비스의 로그 출력을 stream

- 서비스에서 일회성 명령을 실행

**Compose documentation**

- [Compose 설치](http://.com/compose/install/)​

- [시작](https://docs.docker.com/compose/gettingstarted/)

- [Django 로 시작](https://docs.docker.com/compose/django/)​

- [Rails로 시작](https://docs.docker.com/compose/rails/)​

- [WordPress로 시작](https://docs.docker.com/compose/wordpress/)​

- [자주 묻는 질문 \(Q&A\)](https://docs.docker.com/compose/faq/)​

- [명령어 레퍼런스](https://docs.docker.com/compose/reference/)​

- [Compose file 레퍼런스](https://docs.docker.com/compose/compose-file/)​

**특징**

**1. 단일 호스트에 여러 개의 격리된 환경**

Compose는 프로젝트 이름을 사용하여 서로 환경을 분리 합니다. 이 프로젝트 이름을 다른 컨텍스트에서 사용할 수 있습니다.

- dev host에서, 프로젝트의 브랜치의 각각 feature에 대해 안정적인 복사본을 실행할 때와 같이 각각의 단일 환경의 여러 복사본을 만듭니다.

- CI server에서, 서로 간섭하지 않도록 하기 위해 고유한 빌드 넘버로 프로젝트 이름을 셋팅할 수 있습니다.

- 공유된 host 나 dev host를 사용하여 같은 서비스 이름을 사용한 다른 프로젝트에 간섭이 되는 것을 막습니다.

 기본적인 프로젝트 이름은 프로젝트 디렉토리의 basename이다. 프로젝트 이름을 -p [명령어 옵션](https://docs.docker.com/compose/reference/overview/) 또는 COMPOSE\_PROJECT\_NAME [환경 변수](https://docs.docker.com/compose/reference/envvars/#compose-project-name)를 사용하여 프로젝트 이름을 커스텀할 수 있습니다.

**2. 컨테이너를 만들 때 볼륨 데이터를 보존함**

서비스에 의해 사용되어 지는 모든 볼륨을 막을 수 있습니다. docker-compose up명령어를 실행했을 때, docker-compose를 실행하면 이전 실행에서 컨테이너를 찾았을 때, 이 전 컨테이너의 볼륨을 새 컨테이너로 복사를 합니다.

이 프로세스를 통해 볼륨에서 만든 데이터가 손실되지 않도록 합니다.

docker-compose명령어를 윈도우에서 실행을 한다면 [환경변수](https://docs.docker.com/compose/reference/envvars/) 설정이 필요할 수 있습니다.

**3. 변경된 컨테이너만 다시 작성함**

Compose가 컨테이너를 생성하기 위해서 설정을 캐싱해놓습니다.

변경되지 않은 서비스를 재시작 하였을 때 Compose는 기존 컨테이너를 다시 사용합니다.

컨테이너를 다시 사용한다는 것은 환경을 매우 빠르게 변경 할 수 있다는 것을 의미합니다.

**4. 환경 간 구성 변수 및 이동**

Compose는 Compose files 에서 변수를 지원합니다. 이러한 변수를 사용하여 다른 환경 또는 다른 사용자에 대한 Compose를 사용자 정의 할 수 있습니다.

Variable substitution에 대한 자세한 정보는 https://docs.docker.com/compose/compose-file/\#variable-substitution 에서 볼 수 있습니다.

extends필드를 사용하거나 여러 작성 파일을 작성하여 작성한 파일들을 extend할 수 있습니다.

**일반적인 사용 case \(일반적인 사용 예\)**

많은 다른 방법으로 Compose는 사용되어 집니다.

공통적으로 아래의 케이스로 사용합니다.

**개발 환경**

소프트웨어를 개발할 때, 단일의 환경에서 애플리케이션을 실행하고 상호 작용하는 능력은 매우 중요 합니다. Compose 명령어는 환경을 만들고, 이것이 상호작용 하는데 사용되어 집니다.

Compose file은 문서를 작성하는 방법과 모든 서비스의 종속적인 환경\(db, queue, caches, web service API들\)을 제공합니다.

command line tool을 사용하여 single command\(docker-compose up\)를 통해 각각의 의존성있는 하나 또는 수 많은 컨테이너를 만들고, 실행시킵니다.

프로젝트를 시작하기 위해 개발자를 위한 편리한 방법을 제공하는 이점이 있습니다.

Compose는 단일 시스템 Compose파일과 몇가지 명령어로 다양한 개발 시작 가이드를 줄일 수 있습니다. \(개발 환경 셋팅 가이드가 간편해 질 수 있다.\)

**자동화된 테스트 환경**

CD\(Continuous Deployment\) or CI\(Continuous Integration\) 프로세스의 중요한 부분은 자동화된 테스트입니다.

자동화된 end-to-end 테스트에서는 테스트를 실행할 환경이 필요 합니다. Compose는 테스트를 위한 독립된 테스트 환경을 생성하고 destory하는 방법을 제공합니다.

Compose file에서 모든 환경을 정의함으로써, 이러한 환경을 생성하고 destory할 수 있습니다.

```text
$ docker-compose up -d$ ./run_tests$ docker-compose down
```

**단일 host 개발**

 Compose는 전통적으로 workflow 개발 및 테스트에 중점을 두었지만 각 릴리즈마다 더 많은 production-oriented 기능을 발전 시키고 있습니다.

remote 도커 엔진에서 배포를 위해 Compose를 사용합니다.

도커엔진은 도커 머신이나 도커 Swarm클러스터를 통해 제공되어진 단일 인스턴스일 수 있습니다.

production-oriented를 사용하려면 https://docs.docker.com/compose/production/ 애서 확인할 수 있습니다.

