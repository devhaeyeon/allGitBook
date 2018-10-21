# \[도커\] 도커 파헤치기 step2. Webapps with Docker-3

**해당 글은** [**https://github.com/docker/labs/blob/master/beginner/chapters/webapps.md**](https://github.com/docker/labs/blob/master/beginner/chapters/webapps.md) **에서 번역 및 의역을 한 것이므로 정확한 것은 명시한 주소에서 확인할 수 있습니다.**

**해당 실습은**

**단계별로 나눠서 글을 포스팅 합니다.**

**도커 파일에 써보자.**

웹 어플리 케이션과 함께 도커 이미지를 만든다.

이전 포스팅에서 언급이 되었지만 모든 user image는 base image를 기반으로 한다.

해당 실습 애플리케이션은 파이썬으로 작성 되었으므로 [alpine](https://store.docker.com/images/alpine)을 기반으로 파이썬 이미지를 만들고, 도커 파일을 이용 합니다.

​[도커 파일](https://docs.docker.com/engine/reference/builder/)은 도커 데몬이 이미지를 만드는 동안 호출하는 명령어 목록을 포함하는 텍스트 파일 입니다. 도커 파일에는 도커가 앱을 실행하는데 필요한 모든 정보가 들어 있습니다.

도커는 거의 리눅스 환경에서 사용하는 [명령어](https://docs.docker.com/engine/reference/builder/)와 비슷합니다.

그래서 도커의 파일을 만들 때 새로운 문법의 언어를 배울 필요가 없습니다.

1.Dockerfile라 불리는 파이을 만듦니다. 그리고 아래의 내용을 넣습니다.

FROM키워드를 사용하여 base image를 정의 합니다.

> FROM alpine:3.5

2. 일반적으로 파일을 복사하고, 의존성있는 것들을 설치하는 명령을 작성하는 것입니다. 하지만 첫번째로 알파인 리눅스 분산 시스템에 파이썬 pip패키지를 설치할 것입니다. 이렇게 하면 파이썬 인터프리터가 포함된 pip 패키지 뿐만 아니라 다른 의존성 있는 것까지 설치됩니다.

​[RUN](https://docs.docker.com/engine/reference/builder/#run)이라는 명령어를 추가합니다.

> RUN apk add --update py2-pip

3. Flask 애플리케이션을 구성한 파일을 추가합니다.

앱을 실행키기 위해서는 파이선 requirements를 설치합니다.

아래의 내용을 추가하여 구성합니다.

> COPY requirements.txt /usr/src/app/
>
> RUN pip install --no-cache-dir -r /usr/src/app/requirements.txt

​[COPY](https://docs.docker.com/engine/reference/builder/#copy)명령어를 사용하여 이전에 만든 파일을 이미지에 복사합니다.

> COPY app.py /usr/src/app/
>
> COPY templates/index.html /usr/src/app/templates/

4. 노출할 포트를 정의 합니다. flask앱은 5000번 포트에서 실행되기 때문에 500포트로 설정합니다.

> EXPOSE 5000

5. python ./app.py는 간단한 애플리케이션을 실행시키기 위한 명령어이다. 이를 위해 [CMD](https://docs.docker.com/engine/reference/builder/#cmd)를 사용한다.

> CMD \["python", "/usr/src/app/app.py"\]

CMD의 주요 목적은 컨테이너가 시작될 때 기본적으로 실행해야하는 명령어를 컨테이너에 알려주는 것입니다.

6. 도커 파일을 확인합니다.

Dockerfile은 지금 준비가 되어있습니다.

> \# our base image
>
> FROM alpine:3.5
>
> \# Install python and pip
>
> RUN apk add --update py2-pip
>
> \# install Python modules needed by the Python app
>
> COPY requirements.txt /usr/src/app/
>
> RUN pip install --upgrade pip --no-cache-dir -r /usr/src/app/requirements.txt
>
> \# copy files required for the app to run
>
> COPY app.py /usr/src/app/
>
> COPY templates/index.html /usr/src/app/templates/
>
> \# tell the port number the container should expose
>
> EXPOSE 5000
>
> \# run the application
>
> CMD \["python", "/usr/src/app/app.py"\]

\*\* git에서는 RUN pip install --no-cache-dir -r /usr/src/app/requirements.txt

이렇게 나와 있지만 , 해당 부분을 실행하면 업그레이드를 하라는 명령어가 나옴.

**이미지를 빌드하자.**

Dockerfile생성 되어 있다면, 이미지를 빌드할 수 있습니다.

docker build라는 명령어는 도커 파일에서 도커 이미지를 만드는 무거운 전달을 합니다.

dockeer build라는 명령어를 실행할 때, &lt;YOUR\_USERNAME&gt;을 사용자 이름으로 교체해야 합니다.

username은 [Docker Clould](https://cloud.docker.com/)에 등록이 되어진 것과 같아야 합니다.

아직 만들지 않았다면 Docker Clould에 등록하면됩니다.

docker build명령어는 꽤 간단합니다. -t플래그와 함께 tag 옵션으로 가질 수 있고, . 은 도커 파일이 존제하는 디렉토리 위치입니다.

> $ docker build -t &lt;YOUR\_USERNAME&gt;/myfirstapp .

alpine:3.5이미지가 없는 경우에는 클라이언트가 먼저 이미지를 끌어온 다음 이미지를 만듭니다.

그러므로, 명령을 실행한 후의 화면은 사용자마다 다를 수 있습니다.

모든 것을 여기까지 잘 따라 왔다면, 이미지는 준비가 되었습니다.

docker images명령어를 입력하여 실행한 이미지 \(&lt;YOUR\_USERNAME&gt;/myfirstapp\) 가 표시되는지 확인 합니다.

**도커 이미지를 실행하자.**

만든 이미지가 잘 작동하는지 확인합니다.

> $ docker run -p 8888:5000 --name myfirstapp YOUR\_USERNAME/myfirstapp

http://localhost:8888에 주소 입력하면 앱이 라이브되어야합니다.

다른 터미널을 열고 Docker Machine IP기본값을 사용하여 컨테이너 IP 주소를 결정해야할 수도 있습니다.

**도커 이미지를 PUSH**

먼저 도커 클라우도 계정으로 로그인을 합니다.

> docker login

를 입력 후 YOUR\_USERNAME과 password 를 입력합니다.

> docker push YOUR\_USERNAME/myfirstapp

컨테이너를 다 사용하고 사용하지 않는다면 stop 하고 remove를 하면 됩니다.

다른 터미널을 열어서 아래의 명령어를 칩니다.

> $ docker stop myfirstapp
>
> $ docker rm myfirstapp

or

> $ docker rm -f myfirstapp

**Dockerfile 명령어 요약**

Dockerfile에서 사용되어지는 명령어들을 빠르게 요약하려 합니다.

FROM : Dockerfile을 시작합니다. Dockerfile은 FROM명령으로 시작해야 합니다. 이미지는 layer로 작성 됩니다. 즉, 다른 이미지를 base Image로 사용할 수 있습니다. FROM명령은 base\(기본\) layer를 정의 합니다. 인수로 이미지의 이름을 사용합니다. 선택적으로 username/imagename:version 형식에 관리자 및 이미지 버젼의 Docker Clould 사용자 이름을 추가할 수 있습니다.

RUN : 작성중인 이미지를 작성하는데 사용됩니다. 각 RUN명령에 대해 Docker는 명령을 실행한 다음 이미지의 새 계층을 만듭니다. 이렇게 하면 이미지를 이전 상태로 쉽게 롤백할 수 있습니다. RUN명령어의 문법은 RUN 다음에 쉘 명령어의 전체 택스트에 놓는 것입니다. \(ex , RUN mkdir /user/local/foo 여기서 mkdir /user/local/foo은 /user/local에 foo 폴더를 새로 만드는 쉘스크립트 입니다.\) 이는 쉘의 /bin/sh에 자동적으로 실행이 될 것입니다. 'RUN / bin / bash-c 'mkdir / user / local / fo'와 같은 다른 쉘을 정의할 수 있습니다.

COPY : 컨테이너에서 로컬파일을 복사합니다.

CMD : 컨테이너가 시작 시 이미지에서 실행될 명령어를 정의 합니다. RUN과 달리 이미지에 대한 새 layer을 작성하지는 않지만 명령을 실행합니다. Dockerfile/Image당 CMD가 하나만 있을 수 있습니다. 만약 복수개의 명령어를 실행 시켜야 하는 경우, CMD에 스크립트를 실행하도록 하는 것이 가장 좋습니다. CMD는 RUN과 달리 명령을 실행할 위치를 지정 해야 합니다. CMD의 예는 다음과 같습니다.

> CMD \["python", "./app.py"\]
>
>  CMD \["/bin/bash", "echo", "Hello World"\]

EXPOSE : 포트가 서비스를 제공하는 이미지 사용자에 대한 hint를 만듭니다. 이 것은

$ docker inspect &lt;container-id&gt;를 통해 검색하여 알 수 있는 정보에 포함이 되어 있습니다.

" EXPOSE명령은 실제로 호스트에서 액세스할 수 있는 포트를 만들 지 않습니다. 대신 $ docker run 명령어를 사용할 때 -p 플래그를 사용하여 게시를 하여야 합니다. "

PUSH : Docker Cloud에 이미지를 push하거나 즉시 [private registry](https://docs.docker.com/registry/)에 push 합니다.

"만약 도커 파일에 대해서 더 배우고 싶다면, [Best practices for writing Dockerfiles](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)에서 확인하세요"

다음 시간에는 Swarm을 통해 앱을 배포하는 것을 다룹니다.

\(https://github.com/docker/labs/blob/master/beginner/chapters/votingapp.md\)[  
](https://scarlett-dev.gitbook.io/docker-kubernetes/step2.-webapps-with-docker-2)

