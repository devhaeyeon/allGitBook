# \[도커\] 도커 파헤치기 step2. Webapps with Docker-2

**해당 글은** [**https://github.com/docker/labs/blob/master/beginner/chapters/webapps.md**](https://github.com/docker/labs/blob/master/beginner/chapters/webapps.md) **에서 번역 및 의역을 한 것이므로 정확한 것은 명시한 주소에서 확인할 수 있습니다.**

**해당 실습은**

**단계별로 나눠서 글을 포스팅 합니다.**

**첫번째 이미지를 만들어보자 "해당 부분에 사용된 코드는 해당 레지스트리의 flask-app 폴더에 있습니다. \(https://github.com/docker/labs/tree/master/beginner/flask-app\)" 훨씬 더 나은 이미지를 이해하고, 스스로 이미지를 만들어보려고 합니다.** 

**학습 목표는 작은 Flask 애플리케이션의 샌드박스 이미지를 만드는 것입니다.** 

**Flask 애플리케이션을 실행할 도커이미지를 만들기 위해서 연습이 필요합니다.** 

**우리는 파이썬 Flask로된 환경에서 랜덤한 고양이 이미지를 생성하기 위한 컴포넌트를 첫번째로 내려 받고나서 Dockerfile써서 도커라이징합니다.** 

**마지막으로 이미지를 빌드할것이고, 그 다음 실행할 것입니다.** 

**크게 순서는 이렇게 됩니다.** 

**1\) 랜덤한 고양이를 화면에 보여주는 파이썬 Flask앱을 만듭니다.** 

**2\) 도커 파일을 씁니다.** 

**3\) 이미지를 빌드 합니다.** 

**4\) 이미지를 실행 합니다.** 

**5\) Dockerfile commands summary**

**파일들을 만들기 전에 cd flask-app 명령어를 입력하여 폴더를 생성합니다. 왜냐하면 이미지에 임의의 파일들을 모두 추가하지 않기 때문입니다.**

  
**app.py 해당 파일에 아래의 코드를 입력합니다.**

```text
```python
from flask import Flask, render_template
import random

app = Flask(__name__)

# list of cat images
images = [
    "http://ak-hdl.buzzfed.com/static/2013-10/enhanced/webdr05/15/9/anigif_enhanced-buzz-26388-1381844103-11.gif",
    "http://ak-hdl.buzzfed.com/static/2013-10/enhanced/webdr01/15/9/anigif_enhanced-buzz-31540-1381844535-8.gif",
    "http://ak-hdl.buzzfed.com/static/2013-10/enhanced/webdr05/15/9/anigif_enhanced-buzz-26390-1381844163-18.gif",
    "http://ak-hdl.buzzfed.com/static/2013-10/enhanced/webdr06/15/10/anigif_enhanced-buzz-1376-1381846217-0.gif",
    "http://ak-hdl.buzzfed.com/static/2013-10/enhanced/webdr03/15/9/anigif_enhanced-buzz-3391-1381844336-26.gif",
    "http://ak-hdl.buzzfed.com/static/2013-10/enhanced/webdr06/15/10/anigif_enhanced-buzz-29111-1381845968-0.gif",
    "http://ak-hdl.buzzfed.com/static/2013-10/enhanced/webdr03/15/9/anigif_enhanced-buzz-3409-1381844582-13.gif",
    "http://ak-hdl.buzzfed.com/static/2013-10/enhanced/webdr02/15/9/anigif_enhanced-buzz-19667-1381844937-10.gif",
    "http://ak-hdl.buzzfed.com/static/2013-10/enhanced/webdr05/15/9/anigif_enhanced-buzz-26358-1381845043-13.gif",
    "http://ak-hdl.buzzfed.com/static/2013-10/enhanced/webdr06/15/9/anigif_enhanced-buzz-18774-1381844645-6.gif",
    "http://ak-hdl.buzzfed.com/static/2013-10/enhanced/webdr06/15/9/anigif_enhanced-buzz-25158-1381844793-0.gif",
    "http://ak-hdl.buzzfed.com/static/2013-10/enhanced/webdr03/15/10/anigif_enhanced-buzz-11980-1381846269-1.gif"
]

@app.route('/')
def index():
    url = random.choice(images)
    return render_template('index.html', url=url)

if __name__ == "__main__":
    app.run(host="0.0.0.0")
```

```

**requirements.txt** 

**앱에 파이썬 모듈을 설치하기 위해, requirements.txt이라는 파일을 생성하고, 해당 파일에 코드를 집어 넣습니다.**

 **Flask==0.10.1**

**templates/index.html**

**templates라는 폴더를 만들고 그 안에 index.html파일을 생성하고 아래의 내용을 입력합니다.**

```text
```html
<html>
  <head>
    <style type="text/css">
      body {
        background: black;
        color: white;
      }
      div.container {
        max-width: 500px;
        margin: 100px auto;
        border: 20px solid white;
        padding: 10px;
        text-align: center;
      }
      h4 {
        text-transform: uppercase;
      }
    </style>
  </head>
  <body>
    <div class="container">
      <h4>Cat Gif of the day</h4>
      <img src="{{url}}" />
      <p><small>Courtesy: <a href="http://www.buzzfeed.com/copyranter/the-best-cat-gif-post-in-the-history-of-cat-gifs">Buzzfeed</a></small></p>
    </div>
  </body>
</html>
```

```



