# \[도커\] 도커 파헤치기 step1. Running your first container



아래의 글은 번역 혹은 의역을 하였음을 사전에 알려 드립니다 \(관련 수치는 해당 원글을 참고하였습니다.\) \(출처 : [https://github.com/docker/labs/tree/master/beginner](https://github.com/docker/labs/tree/master/beginner)\)

### 서론 <a id="&#xC11C;&#xB860;"></a>

이 글을 보기 전에 도커 설치가 필요합니다. 도커를 설치했다면 이제 힘들고 긴긴 여정이 시작될 것입니다. 이 글에서는 경량화된 리눅스 컨테이너인 알파인을 실행시키고 docker run 명령어를 익힐 것입니다.

> $ docker pull alpine

“도커가 시스템에 설치를 했는데, 위의 명령어를 친 후에 permission denied에러가 날 수도 있습니다. 그럼 [https://docs.docker.com/get-started/](https://docs.docker.com/get-started/) 로가서 해당 튜토리얼 부터 다시 시작하면 됩니다. 만약 리눅스 환경이라면 sudo docker 처럼 ‘sudo’가 필요 합니다. 대신에 이 이슈를 해결하기 위해서는 도커 그룹\([https://docs.docker.com/install/linux/docker-ee/ubuntu/\)을](https://docs.docker.com/install/linux/docker-ee/ubuntu/%29%EC%9D%84) 새로 만들 수 있습니다.”

pull 명령어는 도커 레지스트리에서 부터 시스템에 ‘alpine’ 이미지를 fetch하고 save하는 명령어 입니다. 시스템에 모든 이미지의 리스트를 보려면 docker images라는 명령어를 치면 됩니다.

> $ docer images

### docker Run <a id="docker-Run"></a>

이미지로부터 도커 컨테이너를 run 하기 위해서는 docker run 명령어를 사용합니다.

> $ docker run apline ls -l

run을 하면 내부적으로 수 많은 일들이 일어납니다.

1. 도커 클라이언트는 도커 데몬을 연결합니다.
2. 도커 데몬은 로컬 저장소를 확인합니다. 이미지가 \(여기서는 alpine이미지\) 로컬에서 사용할 수 있는지, Docker Store로부터 다운로드가 가능한지에 대한 여부를 확인합니다.\(docker pull alpine를 하기 전에 문제가 생긴 다면, 다운로드에 실패합니다.\)

docker run alpine를 실행하면, ls -l과 같은 명령어를 입력하면 도커는 지정한 명령어를 실행하고, list하고 있는 것들을 볼수 있습니다.

좀 더 흥미로운 아래의 명령어를 입력해보면

> $docker run alpine echo “hello from alpine”

화면에 “hello from alpine”를 볼 수 있습니다. 이 케이스는 도커 클라이언트가 alpine 컨테이너로 부터 echo 명령어를 실행하고 종료하는 케이스 입니다. 만약 해당 명령어를 이미 실행했었다면, 빠르게 실행이 됩니다. 이미지는 가상 머신을 부팅하고, 명령어를 실행하고, killing합니다. 컨테이너가 훨씬 더 빠른 것을 알 수 있습니다.

> $ docker run apline /bin/sh

기다리면, 아무 것도 발생하지 않습니다. 이건 버그가 아닙니다. 대화식 쉘은 대화식 터미널에서 실행시키지 않는다면, 명령어를 실행한 후 종료 됩니다. \( 그래서 이 예제에서 이 명령어가 종료 되지 않게 하기 위해서는 docker run -it alpine /bin/sh 명령어를 사용합니다.\)

컨테이너 쉘 내부에서는 ls -l, uname -a와 같은 몇몇의 명령어를 사용할 수 있습니다. exit 명령어는 컨테이너를 종료하는 명령어입니다.

docker ps라는 명령어는 최근에 실행된 모든 도커 컨테이너를 보는 명령어입니다.

> $ docker ps

실행되고 있는 컨테이너가 없다면, 빈 줄을 볼 수 있습니다. 유용히 쓰이는 명령어는 ‘docker ps -a’

위의 명령어를 통해 실행했던 모든 컨테이너 목록을 볼 수 있습니다. STATUS 컬럼을 통해 이들 컨테이너가 종료된 시간을 알 수 있습니다.

컨테이너에 하나의 명령어만 입력할 수 있을까요? NO!

> $ docker run -it run alpine /bin/sh / \# ls / \# uname -a

run 명령어에 -it를 플래그를 같이 쓰면 컨테이너에서의 대화식 tty을 사용할 수 있습니다. \(컨테이너에서 여러개의 명령어를 입력하여 사용할 수 있습니다.\)

docker run명령어는 편하고 시간을 단축 시켜주는 가장 자주 사용하는 명령어입니다. run에 대해 훨씬 더 많이 알고 싶으면 docker run –help이라는 명령어를 사용하면 지원하는 모든 플래그 리스트들을 볼 수 있습니다.

도커를 사용하면서 docker run명령어는 자주 보게 될 것 입니다.

### Terminology <a id="Terminology"></a>

수 많은 도커 용어를 볼 수 있는데, 도커 용어에 대해서 설명하려 합니다.

* Image : 파일 시스템과 애플리케이션의 형태는 컨테이너를 생성하여 사용합니다. docker inspect alpine을 실행하면 이에 대한 자세한 것을 알 수 있다. alpine이미지를 다운 받기 위해 docker pull 명령어를 사용할 수 있습니다. docker run hello-world라는 명령어를 실행하면, docker pull이 백그라운드에서 실행되어 hello-world 이미지를 다운 받습니다.
* Container : 도커 이미지의 인스턴스를 실행하면 컨테이너는 실질적인 애플리케이션을 실행합니다. 컨테이너는 애플리케이션, 의존성이 있는 컨테이너들을 포함합니다. 이것은 다른 컨테이너에 있는 커널을 공유하고, 호스트 OS위에 있는 공간에 유저에 있는 연관되어진 프로세스들을 실행합니다. 컨테이너는 다운로드 받아진 alpine 이미지를 docker run 명령어를 통해서 컨테이너가 생성됩니다. docker ps 명령어를 사용하여 실행되어진 컨테이너 리스트를 볼 수 있습니다.
* Docker daemon : 도커 컨테이너를 구축, 실행 및 배포하는 호스트에서 실행되는 백그라운드 서비스입니다.
* Docker client : 도커 데몬과 함께 사용자와 상호 작용할 수 있게 허용하는 명령어 툴입니다.
* Docker Store : 컨테이너, 플러그인 등등 도커 에디션을 찾을 수 있고, 엔터프라이즈에서 사용할 수 있는 도커 이미지 레지스트리이다. \([https://store.docker.com/](https://store.docker.com/)\)

