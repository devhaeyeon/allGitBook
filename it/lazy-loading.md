# Lazy Loading 이란?

### Lazy Loading <a id="LazyLoading-LazyLoading"></a>

#### 0.Overview <a id="LazyLoading-0.Overview"></a>

사용자가 웹 페이지를 열면 전체 페이지의 내용이 다운로드 되어 단일 이동으로 렌더링이 됩니다.

이를 통해 브라우저는 웹페이지를 캐시할 수 있지만 사용자가 다운로드한 모든 콘텐츠를 실제로 볼 수 있다는 보장은 없습니다.

예를 들어 전체 사진 갤러리를 다운로드했지만 사용자가 첫번째 이미지만 본 후 사용자가 떠났을 때 웹페이지에서는 메모리 및 대역폭 낭비로 인해 발생합니다.

페이지에 액세스할 때 모든 콘텐츠를 대량으로 로드하는 대신 사용자가 필요한 페이지의 일부에 액세스할 때 콘텐츠를 로드할 수 있습니다.

lazy loading을 사용하면 페이지가 placeholder 콘텐츠로 작성되며, 사용자가 필요할 때만 실제 콘텐츠로 대체 됩니다.

#### 1. 무엇이며 어떻게 적용이 되는가? <a id="LazyLoading-1.&#xBB34;&#xC5C7;&#xC774;&#xBA70;&#xC5B4;&#xB5BB;&#xAC8C;&#xC801;&#xC6A9;&#xC774;&#xB418;&#xB294;&#xAC00;?"></a>

lazy loading은 페이지를 읽어들이는 시점에 중요하지 않은 리소스 로딩을 추 후에 하는 기술 입니다. 대신에 이 중요하지 않은 리소스들은 필요할 때 로드가 되어야 합니다.

이미지와 관련된 경우에는 중요하지 않은 리소스들은 "off-screen"와 함께 동기화가 됩니다.

누군가가 웹페이지\(이미지, 비디오 등\)에 리소스를 추가할 때, 리소스는 small placeholder를 참조합니다. 사용자가 웹페이지를 검색할 때 실제 리소스는 브라우저에 의해 캐시되고 리소스가 사용자 화면에 표시될 때 placeholder를 대체합니다.

예를 들어, 사용자가 웹페이지를 로드하고 즉시 남겨 두면 웹페이지의 맨 위 부분 이외의 항목이 로드되지 않습니다.

이미지, 비디오를 그냥 로딩하지 않고 lazy loading을 사용하는 이유는 사용자가 볼 수 없는 것들을 로딩할 가능성이 있기 때문입니다.

- 사용자가 보고 있지 않은 것들을 로딩할 때 데이터가 낭비됩니다. 무제한 요금제를 사용하는 사용자인 경우에는 상관이 없지만 제한된 요금제를 사용하는 사용자인 경우 사용자가 보고 있지 않은 화면을 로딩하는 것은 자원\(돈\)을 낭비할 수도 있습니다.

- 미디어 리소스를 다운로드 한 후 브라우저는 이를 디코딩하여 화면에 렌더링 해야 합니다.

#### 2. SEO에 미치는 영향 <a id="LazyLoading-2.SEO&#xC5D0;&#xBBF8;&#xCE58;&#xB294;&#xC601;&#xD5A5;"></a>

lazy loading은 검색 엔진 순위에 영향을 미친다. 리소스는 placeholder 콘텐츠여서 웹사이트를 크롤링하는 검색 엔진은 리소스의 내용을 잘못 해석하거나 무시할 수 있습니다.

블로그 게시물과 같은 웹페이지의 전체 구성 요소를 느리게 로드하면 검색 엔진이 해당 구성 요소를 우회하여 콘텐츠가 인덱싱 되지 않아 검색 엔진 결과가 줄어들 수 있습니다.

이러한 문제를 극복하는 한 가지 요령은 lazy load하는 콘텐츠에 대한 링크를 제공하는 것입니다.

이렇게 하면 기본적으로 검색 엔진 크롤러가 액세스 할 수 있는 콘텐츠에서 웹페이지를 만듭니다.

검색 엔진이 웹사이트를 index하면 이러한 링크를 따라가며 검색한 내용을 색인화 합니다.

이 방법은 기본적으로 사용자가 콘텐츠를 동적으로 로드할 수 있게 하면서 lazy load도 웹사이트를 전통적인 웹사이트로 구성합니다.

#### 3. 예시 <a id="LazyLoading-3.&#xC608;&#xC2DC;"></a>

워드프레스는 infinite scroll이라 불리는 lazy loading솔루션을 제공합니다.

infinite scroll은 사용자가 페이지로 스크롤할 때 지속적으로 로드 합니다.

무한히 로드하는 웹페이지에서 일반적으로 액세스 할 수 없는 footer는 스크롤 하는 내용 아래에 오버레이로 표시 됩니다.

wordpress는 전통적인 페이지 기반 접근 방식과 달리 infinite scroll을 사용할 때 사용자가 더 많은 게시물을 읽습니다.

구글은 이미지 검색 결과에 대해 다른 접근 방식을 취합니다.

사용자가 페이지를 스크롤할 때 placeholder 이미지가 썸네일로 바뀝니다.

특정 수의 이미지가 표시 된 후 button을 누르면 추가 이미지를 로드할 수 있습니다.

button을 사용하여 Google은 무한 스크롤링과 lazy loading을 결합하여 동적 하이브리드 접근법을 만듭니다.

#### 4. 장점 <a id="LazyLoading-4.&#xC7A5;&#xC810;"></a>

1\) lazy loading은 콘텐츠 전달 최적화와 최종 사용자 간의 경험을 간소화 하는 균형을 맞춥니다.

2\) 사용자가 처음 열 때 웹 사이트의 일부만 다운로드 해야하므로 사용자에게 콘텐츠를 더 빨리 제공합니다.

3\) 콘텐츠가 지속적으로 사용자에게 공급되므로 사용자가 웹사이트를 이탈할 확률을 낮출 수 있습니다.

4\) 사용자가 한 번에 필요로 하는 경우에만 콘텐츠를 불러오므로 리소스 비용\(사용자의 배터리, 시간, 시스템 리소스\)이 낮아진다.

#### 5. 웹\(a.k.a 자바스크립트\)에서 적용하는 방법  <a id="LazyLoading-5.&#xC6F9;(a.k.a&#xC790;&#xBC14;&#xC2A4;&#xD06C;&#xB9BD;&#xD2B8;)&#xC5D0;&#xC11C;&#xC801;&#xC6A9;&#xD558;&#xB294;&#xBC29;&#xBC95;"></a>

**: 이미지의 경우**

웹사이트에서 비동기적으로 이미지를 로딩하는 것을 의미하는데 만약 사용자가 스크롤을 페이지 하단까지 하지 않는다면, 이미지들은 페이지 하단에 배치된 이미지가 로드 되지 않습니다.

많은 웹사이트 들이 이런 접근 법을 사용하고 있지만 이미지가 많은 사이트에서는 더욱 자주 보입니다.

페이지에서 스크롤 다운을 했을 때 미리보기를 위한 placeholder image들이 실제 이미지를 빠르게 채워 나갈 것입니다.

예를 들어 unsplash.com이라는 사이트에서 본다면 페이지의 해당 부분을 스크롤하면 placeholder image가 full-res 사진으로 대체됩니다.

일반적인 로직은 이와 같습니다.

1\) 이미지 태그에 src값을 넣지 않고 data-src와 같은 data 어트리 뷰트를 사용하여 해당 data 어트리 뷰트에 실제 로드할 이미지 주소를 기입합니다.

2\) 이미지들을 모두 읽어서 객체에 담습니다.

3\) 해당 이미지가 로드가 완료되면\(onload\) data-src\(data 어트리뷰트\)에 있는 주소 값을 src값으로 셋팅을 하고 data-src어트리 뷰트는 삭제합니다.

**첫번째 방법 : Simple Image Lazy Load and Fade**

David Walsh는 커스텀 스크립트를 제안하였습니다.

마크업에서 img의 src 속성을 data-src속성으로 변경합니다.

레이지로딩이 되는 순간 스타일, 애니메이션을 주고 싶다면 아래의 스타일을 줍니다. img { opacity : 1; transition : opacity 0.3s; } img\[data-src\] { opacity : 0; }

그러고 나서 자바스크립트 코드를 작성해 줍니다.

| `[].forEach.call(document.querySelectorAll('img[data-src]'),function(img){ img.setAttribute('src',img.getAttribute('data-src')); img.onload = function(){ img.removeAttribute('data-src'); };});` |
| :--- |


이 방법은 스크롤 했을 때 로드 하는 방법은 포함 되어 있지 않습니다. 사용자의 스크롤 여부와 관계없이 모든 이미지가 브라우저에 의해 로드됩니다.

이미지가 HTML 콘텐츠 뒤에 로드 되므로 빠른 로드 페이지의 이점을 얻을 수 있습니다.

**두번째 방법 : Progressively Enhanced Lazy Loading**

Robin Osborne는 progressive enhancement를 기반으로 해결책을 제시하였습니다.

이 방법은 javascrpt를 사용하여 수행되는 lazy loading 자체는 일반 html 및 css보다 향상된 것으로 간주 합니다.

왜 progressively enhancement ? 만약 자바스크립트 기반의 해결방법을 사용하여 이미지를 보여준다면, javascript가 비활성화 되거나 오류가 발생하면 어떻게 될까요?

이 경우에는 progressive enhancement없이 이미지가 보여지지 않는 것처럼 보여집니다. 좋지 않습니다.

​[https://codepen.io/rposbo/pen/ONmgVG](https://codepen.io/rposbo/pen/ONmgVG) 에서 osbone의 해결방법을 볼 수 있습니다.

​[https://codepen.io/rposbo/pen/EKmXvo](https://codepen.io/rposbo/pen/EKmXvo) 에서는 자바스크립트가 비활성 되거나 오류가 발생했을 때의 코드 입니다.

 **세번째 방법 : Lagy Load XT jQuery Plugin**

​[https://raw.githubusercontent.com/ressio/lazy-load-xt/master/dist/jqlight.lazyloadxt.min.js](https://raw.githubusercontent.com/ressio/lazy-load-xt/master/dist/jqlight.lazyloadxt.min.js)​

| `<script` `src="jquery.js"></script><script` `src="jquery.lazyloadxt.js></script>` |
| :--- |


해당 라이브러리를 다운\(혹은 cdn이용\)받고 스크립트를 삽입합니다.

| `<img` `data-src="lazy.jpg"` `alt="test image">` |
| :--- |


해당 img 요소에 data-src를 넣어줍니다.

| `$(elements).lazyLoadXT();` |
| :--- |


해당 함수를 호출합니다.

​[https://github.com/ressio/lazy-load-xt](https://github.com/ressio/lazy-load-xt)​

**네번째 방법 : bLazy.js - Vanilla JavaScript Plugin**

bLazy는 경량화된 바닐라 자바스크립트 플러그인 입니다.

| `<img` `class="b-lazy"` `src="placeholder.gif"` `data-src="image.jpg"` `alt="test image">` |
| :--- |


해당 img 요소에 class를 b-lazy를 추가합니다.

src에는 임시이미지\(로딩이 되기전에 보여줄 이미지\)를 넣습니다. http request를 줄이기 위해 inline으로 base64로 변환된 이미지를 넣어 놓는다. 조심하지 않으면 같은 이미지를 사용하는 다음 페이지를 캐싱할 때 좋지 않을 수 있습니다.

data-src속성에 실질적으로 불러올 이미지 주소를 적어줍니다.

|  `var` `bLazy = new` `Blazy( { // option here } );` |
| :--- |


해당 스크립트를 삽입해 줍니다.

bLazy.js demo-page : [http://dinbror.dk/blog/blazy/?ref=demo-page](http://dinbror.dk/blog/blazy/?ref=demo-page)​

​[bLazy.js website :](http://dinbror.dk/blog/blazy/?ref=demo-page) ​[http://dinbror.dk/blazy/](http://dinbror.dk/blazy/)​

​[bLazy.js example :](http://dinbror.dk/blazy/) ​[http://dinbror.dk/blazy/examples/?ref=blog](http://dinbror.dk/blazy/examples/?ref=blog)​

**다섯번째 방법 : Lazy Loading 와 함께 이미지 blur 효과**

Medium에 적용되어져 있는 방식입니다.

다양한 방법으로 효과를 주며 lazy loading을 줄 수 있는데

Craig Buckler이 즐겨쓰는 기술인데, 해당 해결 방법은 모두 좋습니다.

​[https://www.sitepoint.com/how-to-build-your-own-progressive-image-loader/](https://www.sitepoint.com/how-to-build-your-own-progressive-image-loader/)​

에서 자세히 읽을 수 있으며, [https://github.com/craigbuckler/progressive-image.js](https://github.com/craigbuckler/progressive-image.js) 에서 코드를 다운 받아서 볼 수 있습니다.

**기타 라이브러리**

​[https://github.com/aFarkas/lazysizes](https://github.com/aFarkas/lazysizes)​

​[https://github.com/ApoorvSaxena/lozad.js](https://github.com/ApoorvSaxena/lozad.js)​

​[https://github.com/malchata/yall.js](https://github.com/malchata/yall.js)​

​[https://github.com/jasonslyvia/react-lazyload](https://github.com/jasonslyvia/react-lazyload) \(a.k.a 리액트\)

​[https://developers.google.com/web/fundamentals/performance/lazy-loading-guidance/images-and-video/](https://developers.google.com/web/fundamentals/performance/lazy-loading-guidance/images-and-video/)

에서 제안한 이미지 lazy Loading 방법이 있습니다.

**1\) 인라인 이미지 사용**

가장 일반적인 lazy loading 는 img 태그 요소에 사용된 이미지 입니다. 우리가 태그 요소를 lazy loading을 할 경우 자바스크립트를 사용하여 화면에 표시되고 있는지 확인 합니다. 존재하는 경우 src\(혹은 srcset\) 속성에 원하는 이미지 url을 채워 넣습니다.

**2\) Intersection observer사용**

1\)의 방법으로 lazy loading 사용한 경우 scroll 또는 resize 와 같은 이벤트 핸들러를 사용하여 작업을 수행했을 것이다. 이 방법은 브라우저에서 호환되지만 최신 브라우저는 intersection observer api를 통해 요소가 화면에 표시 되는 것을 검사하는 작업을 보다 효율적이고 수행할 수 있습니다.

\(일부 브라우저에서는 Intersetion observer가 지원되지 않습니다. 성능은 떨어지지만 호환성을 더 높은 scroll, resize 이벤ㅌ 핸들러를 사용하여 이미지를 로드하는 방법을 보여주는 방법을 위의 구글링크에서 제안 해주었습니다.\)

Intersection event observer는 요소가 화면에 표시하는 것을 계산하는 코드를 작성하는 대신 관찰자를 등록하기만 하면 되기 때문에 다양한 이벤트 핸들러에 의존하는 코드보다 사용하고 읽는 것이 더 쉽습니다.

우리가 해야할 일은 요소가 화면에 나타낼 때 수행할 작업을 결정하는 것입니다.

lazy loading된 요소에 대한 기본 마크업 패턴을 아래와 같이 가정할 수 있습니다.

```text
<img class="lazy" src="placeholder-image.jpg" data-src="image-to-lazy-load-1x.jpg" data-srcset="image-to-lazy-load-2x.jpg 2x, image-to-lazy-load-1x.jpg 1x" alt="I'm an image!">
```

해당 마크업에서 3가지 부분에 집중합니다.

1. class속성은 자바스크립트에서 요소를 선택할 때 사용합니다.

2. src속성은 페이지가 처음 로드 될 때 표시될 placeholder이미지 url을 참조합니다.

3. data-src및 data-srcset요소는 이미지가 화면 상에 나타날 때 표시할 실제 이미지 url을 담고 있는 placeholder속성입니다.

```text
document.addEventListener("DOMContentLoaded", function() {  var lazyImages = [].slice.call(document.querySelectorAll("img.lazy"));  if ("IntersectionObserver" in window) {    let lazyImageObserver = new IntersectionObserver(function(entries, observer) {      entries.forEach(function(entry) {        if (entry.isIntersecting) {          let lazyImage = entry.target;          lazyImage.src = lazyImage.dataset.src;          lazyImage.srcset = lazyImage.dataset.srcset;          lazyImage.classList.remove("lazy");          lazyImageObserver.unobserve(lazyImage);        }      });    });    lazyImages.forEach(function(lazyImage) {      lazyImageObserver.observe(lazyImage);    });  } else {    // Possibly fall back to a more compatible method here  }});
```

document의 DOMContentLoaded이벤트 에서 DOM에 img 태그이면서 lazy 클래스가 있는 모든 요소를 가져 옵니다.

intersection observer를 사용할 수 있는 경우 img.lazy요소가 화면에 나타날 때 콜백을 실행하는 새 observer를 생성합니다.

\(예제 : [https://codepen.io/malchata/pen/YeMyrQ](https://codepen.io/malchata/pen/YeMyrQ)\)

\(참고 , 이 코드는 isIntersecting라고 명명된 Intersection Observer 메소드를 통해 구현하였으니, IE Edge 15버전의 Intersection observer 구현에서는 사용할 수 없습니다. 따라서 위의 lazy loading 코드는 실패 합니다. [https://github.com/w3c/IntersectionObserver/issues/211](https://github.com/w3c/IntersectionObserver/issues/211) 에서 좀 더 나은 방향의 코드를 확인할 수 있습니다.\)

그러나 Intersection observer의 단점은 브라우저 간에 좋은 지원을 제공하지만 보편적이지 않다는 점입니다. 지원하지 않는 브라우저를 위해 위의 코드에서는

폴리필\([https://github.com/w3c/IntersectionObserver/tree/master/polyfill](https://github.com/w3c/IntersectionObserver/tree/master/polyfill)\)이 필요하고 사용 가능 여부를 검색한 후 이전의 호환되는 방법으로 돌아가야 합니다.

**3\) 이벤트 핸들러 사용 \(가장 호환성이 높음\)**

lazy loading을 위해 Intersection observer를 사용하게 되면 애플리케이션의 요구 사항은 브라우저 호환성이 중요하게 됩니다. 이 때문에 Intersection observer polyfill를 적용할 수 있습니다.\(가장 쉬운 방법\)

하지만 화면에 요소가 표시되는 것을 판단하기 위해 getBoundingClientRect와 함께 scroll과 resize , orientation change 이벤트 핸들러 사용하는 방식으로 되돌아 가야 합니다.

이전과 같은 마크업을 사용하면 다음 코드가 lazy loading기능을 제공합니다.

```text
document.addEventListener("DOMContentLoaded", function() {let lazyImages = [].slice.call(document.querySelectorAll("img.lazy"));  let active = false;  const lazyLoad = function() {    if (active === false) {      active = true;      setTimeout(function() {        lazyImages.forEach(function(lazyImage) {          if ((lazyImage.getBoundingClientRect().top <= window.innerHeight && lazyImage.getBoundingClientRect().bottom >= 0) && getComputedStyle(lazyImage).display !== "none") {            lazyImage.src = lazyImage.dataset.src;            lazyImage.srcset = lazyImage.dataset.srcset;            lazyImage.classList.remove("lazy");            lazyImages = lazyImages.filter(function(image) {              return image !== lazyImage;            });            if (lazyImages.length === 0) {              document.removeEventListener("scroll", lazyLoad);              window.removeEventListener("resize", lazyLoad);              window.removeEventListener("orientationchange", lazyLoad);            }          }        });        active = false;      }, 200);    }  };  document.addEventListener("scroll", lazyLoad);  window.addEventListener("resize", lazyLoad);  window.addEventListener("orientationchange", lazyLoad);});
```

이 코드는 scroll이벤트에서 img.lazy엘리먼트가 화면에 표시되는 지 확인하기 위해 getBoundingClientRect를 사용합니다.

setTimeout은 lazy loading처리를 하기 위해 호출되고 active변수는 상태를 관리하기 위해 사용됩니다. 이미지가 lazy loading되면 엘리먼트 배열에서 삭제 됩니다.

엘리먼트의 길이가 0이 되면 스크롤 이벤트를 제거 합니다.

\(CodePen : [https://codepen.io/malchata/pen/mXoZGx](https://codepen.io/malchata/pen/mXoZGx) \)

이 코드는 대부분의 브라우저에서 동작하지만, 반복적인 setTimeout호출로 인해 성능 문제가 있을 수 있습니다. 이 예제는 이미지가 화면에 표시되고 있는지 여부에 상관없이 스크롤 또는 창 크기 조절 시 200밀리초마다 확인을 합니다.

또한 얼마나 많은 요소가 lazy loading되고 스크롤 이벤트 핸들러의 바인딩이 해제되는지 추적하는 지루한 작업은 우리에게 맡깁니다.

\(우리 = 작업하는 우리 ...개발자 ㅠ\)

따라서 가능하면 교차 관찰자를 사용하고 광범위한 호환성이 중요한 애플리케이션일 때 이벤트 핸들러를 사용하여 구현하여야 합니다.

**4\) CSS안의 이미지**

img 태그는 웹페이지에서 이미지를 사용하는 가장 일반적인 방법이지만 CSS background-image속성\(및 기타 속성\)을 통해 이미지를 호출할 수도 있습니다. img 엘리먼트는 화면에 표시되는 것과 관계없이 로드되는 요소이지만,

css의 image 로딩은 더 많은 추측을 통해 수행됩니다. document와 css객체 모델과 렌더 트리가 내장되어, 브라우저는 css는 외부 리소스를 요청하기 전에 문서에 적용되는 방법을 살펴봅니다.

외부 리소스와 관련된 css 규칙이 현재 문서에 적용되지 않는다고 판단하면 브라우저는 요청하지 않습니다.

speculative behavior는 javascript를 사용하여 요소가 화면에 표시되고 있는지 확인한 다음, CSS에 배경 이미지를 호출하는 스타일이 적용된 클래스 요소에 따라 lazy loading에 사용됩니다. 이로 인해 필요할 때 이미지가 다운로드 됩니다.

```text
<div class="lazy-background">  <h1>Here's a hero heading to get your attention!</h1>  <p>Here's hero copy to convince you to buy a thing!</p>  <a href="/buy-a-thing">Buy a thing!</a></div>
```

큰 이미지가 포함된 요소를 가져오는 코드인데, div.lazy-background클래스는 css에 호출되는 배경 이미지를 포함합니다. 이 예제에서 화면에 표시될 때 visible속성을 추가함으로써 div.lazy-background요소의 div.lazy-background 속성을 격리 시킬 수 있습니다.

```text
.lazy-background {  background-image: url("hero-placeholder.jpg"); /* Placeholder image */}.lazy-background.visible {  background-image: url("hero.jpg"); /* The final image */}
```

이 코드는 intersection observer를 사용하여 엘리먼트가 화면에 표시 디고 있는지 javascript를 이용하여 확인하고 visible클래스를 div.lazy-background엘리먼트에 추가하여 이미지를 로딩합니다.

```text
document.addEventListener("DOMContentLoaded", function() {  var lazyBackgrounds = [].slice.call(document.querySelectorAll(".lazy-background"));  if ("IntersectionObserver" in window) {    let lazyBackgroundObserver = new IntersectionObserver(function(entries, observer) {      entries.forEach(function(entry) {        if (entry.isIntersecting) {          entry.target.classList.add("visible");          lazyBackgroundObserver.unobserve(entry.target);        }      });    });    lazyBackgrounds.forEach(function(lazyBackground) {      lazyBackgroundObserver.observe(lazyBackground);    });  }});
```

주의!! 모든 브라우저가 Intersection observer를 지원하는 것은 아니므로 대체 수단 또는 폴리필을 제공해야 합니다.

\([https://codepen.io/malchata/pen/wyLMpR](https://codepen.io/malchata/pen/wyLMpR)\)

**: 비디오의 경우**

일반적인 상황에서 비디오를 로드할 때는 video 태그를 사용합니다. 이의 로딩속도는 사용 사례에 따라 달라집니다.

​[https://developers.google.com/web/fundamentals/performance/lazy-loading-guidance/images-and-video/](https://developers.google.com/web/fundamentals/performance/lazy-loading-guidance/images-and-video/) 링크에서 각각 사용사례, 해결책에 대해서 논의를 하였습니다.

**1\) 자동 재생이 되지 않는 비디오의 경우**

사용자가 재생을 눌러야 재생되는 비디오\(자동 재생 되지 않는 비디오\)의 경우, video태그에서 preload속성을 지정하는 것이 좋습니다.

```text
<video controls preload="none" poster="one-does-not-simply-placeholder.jpg">  <source src="one-does-not-simply.webm" type="video/webm">  <source src="one-does-not-simply.mp4" type="video/mp4"></video>
```

여기서는 preload속성에 none을 적용하여 브라우저가 비디오 데이터를 사전에 처리하지 못하도록 합니다.

때문에 비디오의 공간을 차지하기 위해 poster속성을 사용하여 video 태그에 placeholder을 지정합니다.

그 이유는 비디오 로드에 대한 기본 동작이 브라우저마다 다를 수 있기 때문입니다.

-Chrome : preload기본 값이 auto이었지만 chrome 64에서는 metadata가 기본값으로 설정됩니다. 그렇지만 데스크탑 버전 크롬에서는 content-range헤더를 사용하여 비디오의 일부를 preload할 수 있습니다. firefox, edge 및 ie11은 유사하게 동작합니다.

-데스크탑 chrome과 마찬가지로 safari의 11.0 데스크탑 버전은 비디오 range를 미리 로드 합니다. 버전 11.2\(현재 safari의 tech preview버전\)에서는 비디오 metadata만 사전 로드 됩니다. ios safari에서는 비디오가 사전 로드 되지 않습니다.

-data saver모드가 켜져 있을 경우, preload기본값은 none입니다.

preload대한 브라우저의 기본 동작은 고정된 것이 아니기 때문에 명시적으로 적는 것이 최선의 방법 입니다. 이 경우 사용자가 재생 눌러야 시작하는 모든 플랫폼에서 preload="none"를 사용하면 비디오 load를 지연시킬 수 있습니다. 그러나 preload속성이 lazy load를 구현하는 유일한 방법은 아닙니다.

비디오 preload를 통한 빠른 재생은 javascript 에서 비디오 재생 작업에 대한 아이디어를 제공할 수 있습니다.

하지만 , gif 이미지 대신 비디오를 사용하고 싶을 때는 유용하지 않습니다.

**2\) gif이미지의 대체 동영상**

움직이는 gif는 광범위한 사용되지만, 여러가지 면에서\(특히 파일크기\) 비디오에 비해 하위 수준입니다. 움직이는 gif는 용량이 몇십 메가바이트까지 커질 수 있습니다. \(비슷한 화질의 비디오는 용량이 훨 씬 더 작습니다.\)

gif대체물로 video 태그를 사용하는 것은 img만큼 간단하지 않습니다.

움직이는 gif에는 다음과 같은 세가지 동작이 있습니다.

- 로드되면 자동으로 재생합니다.

- 항상 그런 것은 아니지만 , 루프가 계속 반복됩니다.

- 오디오 트랙이 없습니다.

video엘리먼트를 사용하여 위의 세가지 특징을 충족하는 방법은 다음과 같습니다.

```text
<video autoplay muted loop playsinline>  <source src="one-does-not-simply.webm" type="video/webm">  <source src="one-does-not-simply.mp4" type="video/mp4"></video>
```

autoplay, muted, loop속성은 따로 값 할당이 필요 없는 속성입니다. playsinline은 ios에서 자동재생을 하기 위해 필요합니다.

이제 플랫폼 전반에 걸쳐 움직이는 gif를 비디오로 재생할 수 없습니다. lazy loading을 구현하려면?

chrome은 비디오를 느리게 로드하지만 모든 브라우저에서 이러한 최적화된 동작을 제공할 수는 없습니다.

사용자와 애플리케이션 요구 사항에 따라 문제를 직접 해결해야 할 수도 있습니다.

```text
<video autoplay muted loop playsinline width="610" height="254" poster="one-does-not-simply.jpg">  <source data-src="one-does-not-simply.webm" type="video/webm">  <source data-src="one-does-not-simply.mp4" type="video/mp4"></video>
```

poster속성이 추가 되었는데 이 속성을 사용하면 video 엘리먼트의 비디오가 지연 로드 될 때까지 공간을 차지할 placeholder이미지를 지정할 수 있습니다. 앞에서 다룬 img lazy loading 예제처럼 각 source 태그의 data-src속성에 동영상 url을 넣어둡니다.

여기서 intersection observer를 기반으로 이미지 lazy loading예제와 유사한 몇가지 javascript 을 사용합니다.

```text
document.addEventListener("DOMContentLoaded", function() {  var lazyVideos = [].slice.call(document.querySelectorAll("video.lazy"));  if ("IntersectionObserver" in window) {    var lazyVideoObserver = new IntersectionObserver(function(entries, observer) {      entries.forEach(function(video) {        if (video.isIntersecting) {          for (var source in video.target.children) {            var videoSource = video.target.children[source];            if (typeof videoSource.tagName === "string" && videoSource.tagName === "SOURCE") {              videoSource.src = videoSource.dataset.src;            }          }          video.target.load();          video.target.classList.remove("lazy");          lazyVideoObserver.unobserve(video.target);        }      });    });    lazyVideos.forEach(function(lazyVideo) {      lazyVideoObserver.observe(lazyVideo);    });  }});
```

video 태그를 lazy loading할 때 모든 자식 source엘리먼트들을 반복하면서 data-src속성을 src속성에 대입합니다. 이를 완료하면 엘리먼트에서 load메서드를 호출하여 비디오 로딩을 발생시키면 autoplay속성에 의해 자동적으로 비디오가 재생됩니다.

이 방법을 사용하면 움직이는 gif대신 비디오를 사용할 수 있으면서 데이터 사용량도 줄이고 지연 로딩을 구현할 수 있게 됩니다.

#### 6. 주의 해야할 사항 <a id="LazyLoading-6.&#xC8FC;&#xC758;&#xD574;&#xC57C;&#xD560;&#xC0AC;&#xD56D;"></a>

이미지 및 비디오를 lazy loading 하는 것은 성능 이점을 가지 수도 있지만 , 잘못 이해 한다면 의도하지 않은 결과를 발생할 수 있습니다.

**1\) 폴드를 기억하라**

\(폴드 : 스크롤 없이 볼 수 있는 영역\)

javascript 를 사용하여 페이지에 있는 모든 미디어 리소스를 lazy loading하는 것이 좋을 수 있지만 이러한 부분을 한번 고려해야합니다.

스크롤 없이 볼 수 있는 폴드 영역에 있는 리소스들은 lazy loading이 되어서는 안됩니다. 이러한 resource는 중요한 점으로 간주되어야 하므로 정상적으로 로딩이 되어야 합니다.

lazy loading을 하는 대신 평범한 방식으로 중요한 resource를 로딩하는 이유는 lazy loading 스크립트가 로딩을 완료하고 실행을 시작하여 DOM이 반응하기 전까지 중요한 자원 리소스들의 lazy loading을 지연시킨다는 점입니다.

스크롤해야 볼 수 있는 부분의 이미지는 괜찮지만 폴드 영역에 위치한 중요한 resource들은 img태그를 사용하는 것이 더 빠릅니다.

물론 웹사이트들이 다양한 크기의 스크린에서 보여지고 있는 요즘은 폴드 영역이 어디에 놓여 있는지 명확하지 않습니다.

노트북에서 폴드 영역이 위에 있다면 모바일 기기에선 아래에 있을 수 있습니다. 모든 상황에서 이 문제를 최적으로 해결하기 위한 최고의 해결책은 없습니다.

페이지의 중요 리소스들을 따로 관리하여 일방적인 방식으로 로드해야 합니다.

또한 lazy load를 발생시키는 폴드 영역의 기준선은 너무 엄격하지 않아도 됩니다.

사용자가 해당 리소스가 있는 부분으로 스크롤하기 전에 이미지가 잘 로드될 수 있도록 폴드 영역 아래로 일정 거리의 버퍼 영역을 설정하는 것이 좋습니다.

예를 들어 Intersection Observer api를 사용하면 새로운 IntersectionObserver 인스턴스를 만들 때 옵션 객체에서 rootMargin속성을 지정할 수 있습니다.

이건 효과적으로 엘리먼트에 버퍼를 주며 , 엘리먼트가 화면에 표시되기 전에 지연 로딩 동작을 수행합니다.

```text
let lazyImageObserver = new IntersectionObserver(function(entries, observer) {  // Lazy loading image code goes here}, {  rootMargin: "0px 0px 256px 0px"});
```

rootMargin에 대한 값이 css의 margin속성 값과 유사하게 보이는 이유는 같은 값이 기 때문입니다. 이 경우 observer 요소의 맨 아래 여백\(기본 적으로 브라우저 뷰포트이지만 root속성을 사용하여 특정 요소로 변경할 수 있습니다.\)을 256픽셀로 확장합니다.

즉, 이미지 요소가 뷰포트에서 256픽셀 이내에 있으면 콜백함수가 실행됩니다. 즉 사용자가 실제로 보기 전에 이미지가 로드되기 시작합니다.

스크롤 이벤트를 사용하여 동일한 효과를 얻으려면 getBoundingtlientRect확인 란을 조정하여 버퍼를 포함시키면 intersection observer를 지원하지 않는 브라우저에서도 동일하게 작동합니다.

**2\) 레이아웃 및 placeholder**

lazy loading미디어는 placeholder를 사용하지 않을 경우 레이아웃을 변경시킬 수 있습니다. 이러한 변화는 사용자를 혼란스럽게 할 수 있으며 시스템 리소스를 소비하고 값 비싼 DOM 레이아웃 작업을 유발할 수 있습니다. 최소한 대상 이미지와 동일한 크기를 차지하는 단색 placeholder나

로드하기 전에 미디어 항목의 내용을 암시하는 LQIP\( [http://www.guypo.com/introducing-lqip-low-quality-image-placeholders/](http://www.guypo.com/introducing-lqip-low-quality-image-placeholders/) \) 또는 SQIP \([https://github.com/technopagan/sqip](https://github.com/technopagan/sqip) \) 와 같은 기술을 사용하는 것이 좋습니다.

img 태그에선 src 속성이 최종 이미지의 URL로 업데이트될 때까지 태그의 위치가 변경되면 안됩니다. video태그에선 이미지 placeholder를 사용하기 위해 poster속성을 사용합니다. 또한 width와 height 속성 모드 img및 video태그에서 사용할 수 있는 속성입니다.

이렇게 하면 미디어가 로드 될 때 placeholder에서 최종 이미지로 전환해도 엘리먼트의 크기가 변경되지 않습니다.

**3\) 이미지 디코딩 지연**

Javascript 에서 큰 이미지를 로딩하여 DOM에 놓으면 기본 스레드가 잠기기 때문에, 디코딩이 발생하는 동안 사용자 인터페이스가 짧은 시간동안 응답하지 않게 됩니다. DOM에 삽입하기 전에 디코드 메서드를 이용한 비동기 이미디 디코딩\([https://medium.com/dailyjs/image-loading-with-image-decode-b03652e7d2d2](https://medium.com/dailyjs/image-loading-with-image-decode-b03652e7d2d2)\)을 사용하면 이러한 문제를 해결할 수 있습니다.

하지만 아직 모든 브라우저에서 사용할 수 없으면 사용하기 전에 먼제 확인해야 합니다.

```text
var newImage = new Image();newImage.src = "my-awesome-image.jpg";if ("decode" in newImage) {  // Fancy decoding logic  newImage.decode().then(function() {    imageContainer.appendChild(newImage);  });} else {  // Regular image load  imageContainer.appendChild(newImage);}
```

\(Codepen 예제 : [https://codepen.io/malchata/pen/WzeZGW](https://codepen.io/malchata/pen/WzeZGW)\)

대부분의 이미지가 작다면 큰 효과는 없지만, 큰 이미지를 지연 로딩하여 DOM에 삽입할 때 분명 효과가 있습니다.

**4\) 로드가 되지 않을 때**

```text
var newImage = new Image();newImage.src = "my-awesome-image.jpg";newImage.onerror = function(){  // Decide what to do on error};newImage.onload = function(){  // Load the image};
```

예를 들어 5분 동안 HTML캐싱 정책이 있다고 가정 했을 때 사용자는 사이트를 방문하거나 사용자가 탭을 연 상태로 오랫동안 있다가 다시 사이트를 탐색하는 경우에 어떤 시점에 재배포가 발생한다고 할 때, 이 배포 중에 이미지 리소스의 이름이 해시 기반으로 변경이 되거나 완전히 제거된다면

사용자가 이미지를 지연 로드할 때는 리소스를 사용할 수 없으므로 오류가 발생하여 이미지가 로드되지 않고 오류가 발생합니다.

비교적 드문 케이스이지만, 지연 로딩이 실패한 경우 백업 계획을 세울 수 있습니다.

**5\) 자바스크립트의 사용 가능성**

javascript를 항상 사용할 수 있다고 가정해서는 안됩니다.

javascript를 사용할 수 없는 경우, 이미지를 지연 로딩하려 할 때 이미지를 보여주는 noscript 태그를 고려해볼 수 있습니다.

가장 간단한 대체 예제는 javascript가 비활성화된 경우 이미지를 제공하기 위해 noscript태그를 사용하는 것입니다.

```text
<!-- An image that eventually gets lazy loaded by JavaScript --><img class="lazy" src="placeholder-image.jpg" data-src="image-to-lazy-load.jpg" alt="I'm an image!"><!-- An image that is shown if JavaScript is turned off --><noscript>  <img src="image-to-lazy-load.jpg" alt="I'm an image!"></noscript>
```

javascript 를 사용할 수 없으면 위의 예제는 placeholder 이미지와 noscript태그에 포함된 이미지가 모두 표시 됩니다, 이 문제를 해결하기 위해 html태그에 no-js클래스를 다음과 같이 배치할 수 있습니다.

| `<html class="no-js">` |
| :--- |


그런 다음 javascript가 사용가능한 경우 html 엘리먼트에서 no-js클래스를 제거하는 코드를 head 태그 안에 넣습니다. 다만 스타일 시트를 요청하는 link태그 앞에 배치 합니다.

| `<script>document.documentElement.classList.remove("no-js");</script>` |
| :--- |


마지막으로 css를 사용하여 javascript를 사용할 수 없을 때 lazy loading에 사용하는 클래스로 엘리먼트를 숨길 수 있습니다.

| `.no-js .lazy { display: none;}` |
| :--- |


이렇게 하면 placeholder이미지가 로드 되지 않지만 결과가 더 바람직합니다. javascript를 사용할 수 없는 사용자는 placeholder이미지를 볼 순 없지만 실제 이미지를 볼 수 있습니다.

#### 7. 참고 사이트 <a id="LazyLoading-7.&#xCC38;&#xACE0;&#xC0AC;&#xC774;&#xD2B8;"></a>

아래의 사이트들에서 의역한 내용을 바탕으로 해당 글을 작성 하였습니다.

\(완료\) [https://blog.stackpath.com/glossary/lazy-loading/](https://blog.stackpath.com/glossary/lazy-loading/)

\(완료\) [https://developers.google.com/web/fundamentals/performance/lazy-loading-guidance/images-and-video/](https://developers.google.com/web/fundamentals/performance/lazy-loading-guidance/images-and-video/)​

\(완료\) [https://www.sitepoint.com/five-techniques-lazy-load-images-website-performance/](https://www.sitepoint.com/five-techniques-lazy-load-images-website-performance/)​Lazy Loading

#### 0.Overview <a id="LazyLoading-0.Overview"></a>

사용자가 웹 페이지를 열면 전체 페이지의 내용이 다운로드 되어 단일 이동으로 렌더링이 됩니다.

이를 통해 브라우저는 웹페이지를 캐시할 수 있지만 사용자가 다운로드한 모든 콘텐츠를 실제로 볼 수 있다는 보장은 없습니다.

예를 들어 전체 사진 갤러리를 다운로드했지만 사용자가 첫번째 이미지만 본 후 사용자가 떠났을 때 웹페이지에서는 메모리 및 대역폭 낭비로 인해 발생합니다.

페이지에 액세스할 때 모든 콘텐츠를 대량으로 로드하는 대신 사용자가 필요한 페이지의 일부에 액세스할 때 콘텐츠를 로드할 수 있습니다.

lazy loading을 사용하면 페이지가 placeholder 콘텐츠로 작성되며, 사용자가 필요할 때만 실제 콘텐츠로 대체 됩니다.

#### 1. 무엇이며 어떻게 적용이 되는가? <a id="LazyLoading-1.&#xBB34;&#xC5C7;&#xC774;&#xBA70;&#xC5B4;&#xB5BB;&#xAC8C;&#xC801;&#xC6A9;&#xC774;&#xB418;&#xB294;&#xAC00;?"></a>

lazy loading은 페이지를 읽어들이는 시점에 중요하지 않은 리소스 로딩을 추 후에 하는 기술 입니다. 대신에 이 중요하지 않은 리소스들은 필요할 때 로드가 되어야 합니다.

이미지와 관련된 경우에는 중요하지 않은 리소스들은 "off-screen"와 함께 동기화가 됩니다.

누군가가 웹페이지\(이미지, 비디오 등\)에 리소스를 추가할 때, 리소스는 small placeholder를 참조합니다. 사용자가 웹페이지를 검색할 때 실제 리소스는 브라우저에 의해 캐시되고 리소스가 사용자 화면에 표시될 때 placeholder를 대체합니다.

예를 들어, 사용자가 웹페이지를 로드하고 즉시 남겨 두면 웹페이지의 맨 위 부분 이외의 항목이 로드되지 않습니다.

이미지, 비디오를 그냥 로딩하지 않고 lazy loading을 사용하는 이유는 사용자가 볼 수 없는 것들을 로딩할 가능성이 있기 때문입니다.

- 사용자가 보고 있지 않은 것들을 로딩할 때 데이터가 낭비됩니다. 무제한 요금제를 사용하는 사용자인 경우에는 상관이 없지만 제한된 요금제를 사용하는 사용자인 경우 사용자가 보고 있지 않은 화면을 로딩하는 것은 자원\(돈\)을 낭비할 수도 있습니다.

- 미디어 리소스를 다운로드 한 후 브라우저는 이를 디코딩하여 화면에 렌더링 해야 합니다.

#### 2. SEO에 미치는 영향 <a id="LazyLoading-2.SEO&#xC5D0;&#xBBF8;&#xCE58;&#xB294;&#xC601;&#xD5A5;"></a>

lazy loading은 검색 엔진 순위에 영향을 미친다. 리소스는 placeholder 콘텐츠여서 웹사이트를 크롤링하는 검색 엔진은 리소스의 내용을 잘못 해석하거나 무시할 수 있습니다.

블로그 게시물과 같은 웹페이지의 전체 구성 요소를 느리게 로드하면 검색 엔진이 해당 구성 요소를 우회하여 콘텐츠가 인덱싱 되지 않아 검색 엔진 결과가 줄어들 수 있습니다.

이러한 문제를 극복하는 한 가지 요령은 lazy load하는 콘텐츠에 대한 링크를 제공하는 것입니다.

이렇게 하면 기본적으로 검색 엔진 크롤러가 액세스 할 수 있는 콘텐츠에서 웹페이지를 만듭니다.

검색 엔진이 웹사이트를 index하면 이러한 링크를 따라가며 검색한 내용을 색인화 합니다.

이 방법은 기본적으로 사용자가 콘텐츠를 동적으로 로드할 수 있게 하면서 lazy load도 웹사이트를 전통적인 웹사이트로 구성합니다.

#### 3. 예시 <a id="LazyLoading-3.&#xC608;&#xC2DC;"></a>

워드프레스는 infinite scroll이라 불리는 lazy loading솔루션을 제공합니다.

infinite scroll은 사용자가 페이지로 스크롤할 때 지속적으로 로드 합니다.

무한히 로드하는 웹페이지에서 일반적으로 액세스 할 수 없는 footer는 스크롤 하는 내용 아래에 오버레이로 표시 됩니다.

wordpress는 전통적인 페이지 기반 접근 방식과 달리 infinite scroll을 사용할 때 사용자가 더 많은 게시물을 읽습니다.

구글은 이미지 검색 결과에 대해 다른 접근 방식을 취합니다.

사용자가 페이지를 스크롤할 때 placeholder 이미지가 썸네일로 바뀝니다.

특정 수의 이미지가 표시 된 후 button을 누르면 추가 이미지를 로드할 수 있습니다.

button을 사용하여 Google은 무한 스크롤링과 lazy loading을 결합하여 동적 하이브리드 접근법을 만듭니다.

#### 4. 장점 <a id="LazyLoading-4.&#xC7A5;&#xC810;"></a>

1\) lazy loading은 콘텐츠 전달 최적화와 최종 사용자 간의 경험을 간소화 하는 균형을 맞춥니다.

2\) 사용자가 처음 열 때 웹 사이트의 일부만 다운로드 해야하므로 사용자에게 콘텐츠를 더 빨리 제공합니다.

3\) 콘텐츠가 지속적으로 사용자에게 공급되므로 사용자가 웹사이트를 이탈할 확률을 낮출 수 있습니다.

4\) 사용자가 한 번에 필요로 하는 경우에만 콘텐츠를 불러오므로 리소스 비용\(사용자의 배터리, 시간, 시스템 리소스\)이 낮아진다.

#### 5. 웹\(a.k.a 자바스크립트\)에서 적용하는 방법  <a id="LazyLoading-5.&#xC6F9;(a.k.a&#xC790;&#xBC14;&#xC2A4;&#xD06C;&#xB9BD;&#xD2B8;)&#xC5D0;&#xC11C;&#xC801;&#xC6A9;&#xD558;&#xB294;&#xBC29;&#xBC95;"></a>

**: 이미지의 경우**

웹사이트에서 비동기적으로 이미지를 로딩하는 것을 의미하는데 만약 사용자가 스크롤을 페이지 하단까지 하지 않는다면, 이미지들은 페이지 하단에 배치된 이미지가 로드 되지 않습니다.

많은 웹사이트 들이 이런 접근 법을 사용하고 있지만 이미지가 많은 사이트에서는 더욱 자주 보입니다.

페이지에서 스크롤 다운을 했을 때 미리보기를 위한 placeholder image들이 실제 이미지를 빠르게 채워 나갈 것입니다.

예를 들어 unsplash.com이라는 사이트에서 본다면 페이지의 해당 부분을 스크롤하면 placeholder image가 full-res 사진으로 대체됩니다.

일반적인 로직은 이와 같습니다.

1\) 이미지 태그에 src값을 넣지 않고 data-src와 같은 data 어트리 뷰트를 사용하여 해당 data 어트리 뷰트에 실제 로드할 이미지 주소를 기입합니다.

2\) 이미지들을 모두 읽어서 객체에 담습니다.

3\) 해당 이미지가 로드가 완료되면\(onload\) data-src\(data 어트리뷰트\)에 있는 주소 값을 src값으로 셋팅을 하고 data-src어트리 뷰트는 삭제합니다.

**첫번째 방법 : Simple Image Lazy Load and Fade**

David Walsh는 커스텀 스크립트를 제안하였습니다.

마크업에서 img의 src 속성을 data-src속성으로 변경합니다.

레이지로딩이 되는 순간 스타일, 애니메이션을 주고 싶다면 아래의 스타일을 줍니다. img { opacity : 1; transition : opacity 0.3s; } img\[data-src\] { opacity : 0; }

그러고 나서 자바스크립트 코드를 작성해 줍니다.

| `[].forEach.call(document.querySelectorAll('img[data-src]'),function(img){ img.setAttribute('src',img.getAttribute('data-src')); img.onload = function(){ img.removeAttribute('data-src'); };});` |
| :--- |


이 방법은 스크롤 했을 때 로드 하는 방법은 포함 되어 있지 않습니다. 사용자의 스크롤 여부와 관계없이 모든 이미지가 브라우저에 의해 로드됩니다.

이미지가 HTML 콘텐츠 뒤에 로드 되므로 빠른 로드 페이지의 이점을 얻을 수 있습니다.

**두번째 방법 : Progressively Enhanced Lazy Loading**

Robin Osborne는 progressive enhancement를 기반으로 해결책을 제시하였습니다.

이 방법은 javascrpt를 사용하여 수행되는 lazy loading 자체는 일반 html 및 css보다 향상된 것으로 간주 합니다.

왜 progressively enhancement ? 만약 자바스크립트 기반의 해결방법을 사용하여 이미지를 보여준다면, javascript가 비활성화 되거나 오류가 발생하면 어떻게 될까요?

이 경우에는 progressive enhancement없이 이미지가 보여지지 않는 것처럼 보여집니다. 좋지 않습니다.

​[https://codepen.io/rposbo/pen/ONmgVG](https://codepen.io/rposbo/pen/ONmgVG) 에서 osbone의 해결방법을 볼 수 있습니다.

​[https://codepen.io/rposbo/pen/EKmXvo](https://codepen.io/rposbo/pen/EKmXvo) 에서는 자바스크립트가 비활성 되거나 오류가 발생했을 때의 코드 입니다.

 **세번째 방법 : Lagy Load XT jQuery Plugin**

​[https://raw.githubusercontent.com/ressio/lazy-load-xt/master/dist/jqlight.lazyloadxt.min.js](https://raw.githubusercontent.com/ressio/lazy-load-xt/master/dist/jqlight.lazyloadxt.min.js)​

| `<script` `src="jquery.js"></script><script` `src="jquery.lazyloadxt.js></script>` |
| :--- |


해당 라이브러리를 다운\(혹은 cdn이용\)받고 스크립트를 삽입합니다.

| `<img` `data-src="lazy.jpg"` `alt="test image">` |
| :--- |


해당 img 요소에 data-src를 넣어줍니다.

| `$(elements).lazyLoadXT();` |
| :--- |


해당 함수를 호출합니다.

​[https://github.com/ressio/lazy-load-xt](https://github.com/ressio/lazy-load-xt)​

**네번째 방법 : bLazy.js - Vanilla JavaScript Plugin**

bLazy는 경량화된 바닐라 자바스크립트 플러그인 입니다.

| `<img` `class="b-lazy"` `src="placeholder.gif"` `data-src="image.jpg"` `alt="test image">` |
| :--- |


해당 img 요소에 class를 b-lazy를 추가합니다.

src에는 임시이미지\(로딩이 되기전에 보여줄 이미지\)를 넣습니다. http request를 줄이기 위해 inline으로 base64로 변환된 이미지를 넣어 놓는다. 조심하지 않으면 같은 이미지를 사용하는 다음 페이지를 캐싱할 때 좋지 않을 수 있습니다.

data-src속성에 실질적으로 불러올 이미지 주소를 적어줍니다.

|  `var` `bLazy = new` `Blazy( { // option here } );` |
| :--- |


해당 스크립트를 삽입해 줍니다.

bLazy.js demo-page : [http://dinbror.dk/blog/blazy/?ref=demo-page](http://dinbror.dk/blog/blazy/?ref=demo-page)​

​[bLazy.js website :](http://dinbror.dk/blog/blazy/?ref=demo-page) ​[http://dinbror.dk/blazy/](http://dinbror.dk/blazy/)​

​[bLazy.js example :](http://dinbror.dk/blazy/) ​[http://dinbror.dk/blazy/examples/?ref=blog](http://dinbror.dk/blazy/examples/?ref=blog)​

**다섯번째 방법 : Lazy Loading 와 함께 이미지 blur 효과**

Medium에 적용되어져 있는 방식입니다.

다양한 방법으로 효과를 주며 lazy loading을 줄 수 있는데

Craig Buckler이 즐겨쓰는 기술인데, 해당 해결 방법은 모두 좋습니다.

​[https://www.sitepoint.com/how-to-build-your-own-progressive-image-loader/](https://www.sitepoint.com/how-to-build-your-own-progressive-image-loader/)​

에서 자세히 읽을 수 있으며, [https://github.com/craigbuckler/progressive-image.js](https://github.com/craigbuckler/progressive-image.js) 에서 코드를 다운 받아서 볼 수 있습니다.

**기타 라이브러리**

​[https://github.com/aFarkas/lazysizes](https://github.com/aFarkas/lazysizes)​

​[https://github.com/ApoorvSaxena/lozad.js](https://github.com/ApoorvSaxena/lozad.js)​

​[https://github.com/malchata/yall.js](https://github.com/malchata/yall.js)​

​[https://github.com/jasonslyvia/react-lazyload](https://github.com/jasonslyvia/react-lazyload) \(a.k.a 리액트\)

​[https://developers.google.com/web/fundamentals/performance/lazy-loading-guidance/images-and-video/](https://developers.google.com/web/fundamentals/performance/lazy-loading-guidance/images-and-video/)

에서 제안한 이미지 lazy Loading 방법이 있습니다.

**1\) 인라인 이미지 사용**

가장 일반적인 lazy loading 는 img 태그 요소에 사용된 이미지 입니다. 우리가 태그 요소를 lazy loading을 할 경우 자바스크립트를 사용하여 화면에 표시되고 있는지 확인 합니다. 존재하는 경우 src\(혹은 srcset\) 속성에 원하는 이미지 url을 채워 넣습니다.

**2\) Intersection observer사용**

1\)의 방법으로 lazy loading 사용한 경우 scroll 또는 resize 와 같은 이벤트 핸들러를 사용하여 작업을 수행했을 것이다. 이 방법은 브라우저에서 호환되지만 최신 브라우저는 intersection observer api를 통해 요소가 화면에 표시 되는 것을 검사하는 작업을 보다 효율적이고 수행할 수 있습니다.

\(일부 브라우저에서는 Intersetion observer가 지원되지 않습니다. 성능은 떨어지지만 호환성을 더 높은 scroll, resize 이벤ㅌ 핸들러를 사용하여 이미지를 로드하는 방법을 보여주는 방법을 위의 구글링크에서 제안 해주었습니다.\)

Intersection event observer는 요소가 화면에 표시하는 것을 계산하는 코드를 작성하는 대신 관찰자를 등록하기만 하면 되기 때문에 다양한 이벤트 핸들러에 의존하는 코드보다 사용하고 읽는 것이 더 쉽습니다.

우리가 해야할 일은 요소가 화면에 나타낼 때 수행할 작업을 결정하는 것입니다.

lazy loading된 요소에 대한 기본 마크업 패턴을 아래와 같이 가정할 수 있습니다.

```text
<img class="lazy" src="placeholder-image.jpg" data-src="image-to-lazy-load-1x.jpg" data-srcset="image-to-lazy-load-2x.jpg 2x, image-to-lazy-load-1x.jpg 1x" alt="I'm an image!">
```

해당 마크업에서 3가지 부분에 집중합니다.

1. class속성은 자바스크립트에서 요소를 선택할 때 사용합니다.

2. src속성은 페이지가 처음 로드 될 때 표시될 placeholder이미지 url을 참조합니다.

3. data-src및 data-srcset요소는 이미지가 화면 상에 나타날 때 표시할 실제 이미지 url을 담고 있는 placeholder속성입니다.

```text
document.addEventListener("DOMContentLoaded", function() {  var lazyImages = [].slice.call(document.querySelectorAll("img.lazy"));  if ("IntersectionObserver" in window) {    let lazyImageObserver = new IntersectionObserver(function(entries, observer) {      entries.forEach(function(entry) {        if (entry.isIntersecting) {          let lazyImage = entry.target;          lazyImage.src = lazyImage.dataset.src;          lazyImage.srcset = lazyImage.dataset.srcset;          lazyImage.classList.remove("lazy");          lazyImageObserver.unobserve(lazyImage);        }      });    });    lazyImages.forEach(function(lazyImage) {      lazyImageObserver.observe(lazyImage);    });  } else {    // Possibly fall back to a more compatible method here  }});
```

document의 DOMContentLoaded이벤트 에서 DOM에 img 태그이면서 lazy 클래스가 있는 모든 요소를 가져 옵니다.

intersection observer를 사용할 수 있는 경우 img.lazy요소가 화면에 나타날 때 콜백을 실행하는 새 observer를 생성합니다.

\(예제 : [https://codepen.io/malchata/pen/YeMyrQ](https://codepen.io/malchata/pen/YeMyrQ)\)

\(참고 , 이 코드는 isIntersecting라고 명명된 Intersection Observer 메소드를 통해 구현하였으니, IE Edge 15버전의 Intersection observer 구현에서는 사용할 수 없습니다. 따라서 위의 lazy loading 코드는 실패 합니다. [https://github.com/w3c/IntersectionObserver/issues/211](https://github.com/w3c/IntersectionObserver/issues/211) 에서 좀 더 나은 방향의 코드를 확인할 수 있습니다.\)

그러나 Intersection observer의 단점은 브라우저 간에 좋은 지원을 제공하지만 보편적이지 않다는 점입니다. 지원하지 않는 브라우저를 위해 위의 코드에서는

폴리필\([https://github.com/w3c/IntersectionObserver/tree/master/polyfill](https://github.com/w3c/IntersectionObserver/tree/master/polyfill)\)이 필요하고 사용 가능 여부를 검색한 후 이전의 호환되는 방법으로 돌아가야 합니다.

**3\) 이벤트 핸들러 사용 \(가장 호환성이 높음\)**

lazy loading을 위해 Intersection observer를 사용하게 되면 애플리케이션의 요구 사항은 브라우저 호환성이 중요하게 됩니다. 이 때문에 Intersection observer polyfill를 적용할 수 있습니다.\(가장 쉬운 방법\)

하지만 화면에 요소가 표시되는 것을 판단하기 위해 getBoundingClientRect와 함께 scroll과 resize , orientation change 이벤트 핸들러 사용하는 방식으로 되돌아 가야 합니다.

이전과 같은 마크업을 사용하면 다음 코드가 lazy loading기능을 제공합니다.

```text
document.addEventListener("DOMContentLoaded", function() {let lazyImages = [].slice.call(document.querySelectorAll("img.lazy"));  let active = false;  const lazyLoad = function() {    if (active === false) {      active = true;      setTimeout(function() {        lazyImages.forEach(function(lazyImage) {          if ((lazyImage.getBoundingClientRect().top <= window.innerHeight && lazyImage.getBoundingClientRect().bottom >= 0) && getComputedStyle(lazyImage).display !== "none") {            lazyImage.src = lazyImage.dataset.src;            lazyImage.srcset = lazyImage.dataset.srcset;            lazyImage.classList.remove("lazy");            lazyImages = lazyImages.filter(function(image) {              return image !== lazyImage;            });            if (lazyImages.length === 0) {              document.removeEventListener("scroll", lazyLoad);              window.removeEventListener("resize", lazyLoad);              window.removeEventListener("orientationchange", lazyLoad);            }          }        });        active = false;      }, 200);    }  };  document.addEventListener("scroll", lazyLoad);  window.addEventListener("resize", lazyLoad);  window.addEventListener("orientationchange", lazyLoad);});
```

이 코드는 scroll이벤트에서 img.lazy엘리먼트가 화면에 표시되는 지 확인하기 위해 getBoundingClientRect를 사용합니다.

setTimeout은 lazy loading처리를 하기 위해 호출되고 active변수는 상태를 관리하기 위해 사용됩니다. 이미지가 lazy loading되면 엘리먼트 배열에서 삭제 됩니다.

엘리먼트의 길이가 0이 되면 스크롤 이벤트를 제거 합니다.

\(CodePen : [https://codepen.io/malchata/pen/mXoZGx](https://codepen.io/malchata/pen/mXoZGx) \)

이 코드는 대부분의 브라우저에서 동작하지만, 반복적인 setTimeout호출로 인해 성능 문제가 있을 수 있습니다. 이 예제는 이미지가 화면에 표시되고 있는지 여부에 상관없이 스크롤 또는 창 크기 조절 시 200밀리초마다 확인을 합니다.

또한 얼마나 많은 요소가 lazy loading되고 스크롤 이벤트 핸들러의 바인딩이 해제되는지 추적하는 지루한 작업은 우리에게 맡깁니다.

\(우리 = 작업하는 우리 ...개발자 ㅠ\)

따라서 가능하면 교차 관찰자를 사용하고 광범위한 호환성이 중요한 애플리케이션일 때 이벤트 핸들러를 사용하여 구현하여야 합니다.

**4\) CSS안의 이미지**

img 태그는 웹페이지에서 이미지를 사용하는 가장 일반적인 방법이지만 CSS background-image속성\(및 기타 속성\)을 통해 이미지를 호출할 수도 있습니다. img 엘리먼트는 화면에 표시되는 것과 관계없이 로드되는 요소이지만,

css의 image 로딩은 더 많은 추측을 통해 수행됩니다. document와 css객체 모델과 렌더 트리가 내장되어, 브라우저는 css는 외부 리소스를 요청하기 전에 문서에 적용되는 방법을 살펴봅니다.

외부 리소스와 관련된 css 규칙이 현재 문서에 적용되지 않는다고 판단하면 브라우저는 요청하지 않습니다.

speculative behavior는 javascript를 사용하여 요소가 화면에 표시되고 있는지 확인한 다음, CSS에 배경 이미지를 호출하는 스타일이 적용된 클래스 요소에 따라 lazy loading에 사용됩니다. 이로 인해 필요할 때 이미지가 다운로드 됩니다.

```text
<div class="lazy-background">  <h1>Here's a hero heading to get your attention!</h1>  <p>Here's hero copy to convince you to buy a thing!</p>  <a href="/buy-a-thing">Buy a thing!</a></div>
```

큰 이미지가 포함된 요소를 가져오는 코드인데, div.lazy-background클래스는 css에 호출되는 배경 이미지를 포함합니다. 이 예제에서 화면에 표시될 때 visible속성을 추가함으로써 div.lazy-background요소의 div.lazy-background 속성을 격리 시킬 수 있습니다.

```text
.lazy-background {  background-image: url("hero-placeholder.jpg"); /* Placeholder image */}.lazy-background.visible {  background-image: url("hero.jpg"); /* The final image */}
```

이 코드는 intersection observer를 사용하여 엘리먼트가 화면에 표시 디고 있는지 javascript를 이용하여 확인하고 visible클래스를 div.lazy-background엘리먼트에 추가하여 이미지를 로딩합니다.

```text
document.addEventListener("DOMContentLoaded", function() {  var lazyBackgrounds = [].slice.call(document.querySelectorAll(".lazy-background"));  if ("IntersectionObserver" in window) {    let lazyBackgroundObserver = new IntersectionObserver(function(entries, observer) {      entries.forEach(function(entry) {        if (entry.isIntersecting) {          entry.target.classList.add("visible");          lazyBackgroundObserver.unobserve(entry.target);        }      });    });    lazyBackgrounds.forEach(function(lazyBackground) {      lazyBackgroundObserver.observe(lazyBackground);    });  }});
```

주의!! 모든 브라우저가 Intersection observer를 지원하는 것은 아니므로 대체 수단 또는 폴리필을 제공해야 합니다.

\([https://codepen.io/malchata/pen/wyLMpR](https://codepen.io/malchata/pen/wyLMpR)\)

**: 비디오의 경우**

일반적인 상황에서 비디오를 로드할 때는 video 태그를 사용합니다. 이의 로딩속도는 사용 사례에 따라 달라집니다.

​[https://developers.google.com/web/fundamentals/performance/lazy-loading-guidance/images-and-video/](https://developers.google.com/web/fundamentals/performance/lazy-loading-guidance/images-and-video/) 링크에서 각각 사용사례, 해결책에 대해서 논의를 하였습니다.

**1\) 자동 재생이 되지 않는 비디오의 경우**

사용자가 재생을 눌러야 재생되는 비디오\(자동 재생 되지 않는 비디오\)의 경우, video태그에서 preload속성을 지정하는 것이 좋습니다.

```text
<video controls preload="none" poster="one-does-not-simply-placeholder.jpg">  <source src="one-does-not-simply.webm" type="video/webm">  <source src="one-does-not-simply.mp4" type="video/mp4"></video>
```

여기서는 preload속성에 none을 적용하여 브라우저가 비디오 데이터를 사전에 처리하지 못하도록 합니다.

때문에 비디오의 공간을 차지하기 위해 poster속성을 사용하여 video 태그에 placeholder을 지정합니다.

그 이유는 비디오 로드에 대한 기본 동작이 브라우저마다 다를 수 있기 때문입니다.

-Chrome : preload기본 값이 auto이었지만 chrome 64에서는 metadata가 기본값으로 설정됩니다. 그렇지만 데스크탑 버전 크롬에서는 content-range헤더를 사용하여 비디오의 일부를 preload할 수 있습니다. firefox, edge 및 ie11은 유사하게 동작합니다.

-데스크탑 chrome과 마찬가지로 safari의 11.0 데스크탑 버전은 비디오 range를 미리 로드 합니다. 버전 11.2\(현재 safari의 tech preview버전\)에서는 비디오 metadata만 사전 로드 됩니다. ios safari에서는 비디오가 사전 로드 되지 않습니다.

-data saver모드가 켜져 있을 경우, preload기본값은 none입니다.

preload대한 브라우저의 기본 동작은 고정된 것이 아니기 때문에 명시적으로 적는 것이 최선의 방법 입니다. 이 경우 사용자가 재생 눌러야 시작하는 모든 플랫폼에서 preload="none"를 사용하면 비디오 load를 지연시킬 수 있습니다. 그러나 preload속성이 lazy load를 구현하는 유일한 방법은 아닙니다.

비디오 preload를 통한 빠른 재생은 javascript 에서 비디오 재생 작업에 대한 아이디어를 제공할 수 있습니다.

하지만 , gif 이미지 대신 비디오를 사용하고 싶을 때는 유용하지 않습니다.

**2\) gif이미지의 대체 동영상**

움직이는 gif는 광범위한 사용되지만, 여러가지 면에서\(특히 파일크기\) 비디오에 비해 하위 수준입니다. 움직이는 gif는 용량이 몇십 메가바이트까지 커질 수 있습니다. \(비슷한 화질의 비디오는 용량이 훨 씬 더 작습니다.\)

gif대체물로 video 태그를 사용하는 것은 img만큼 간단하지 않습니다.

움직이는 gif에는 다음과 같은 세가지 동작이 있습니다.

- 로드되면 자동으로 재생합니다.

- 항상 그런 것은 아니지만 , 루프가 계속 반복됩니다.

- 오디오 트랙이 없습니다.

video엘리먼트를 사용하여 위의 세가지 특징을 충족하는 방법은 다음과 같습니다.

```text
<video autoplay muted loop playsinline>  <source src="one-does-not-simply.webm" type="video/webm">  <source src="one-does-not-simply.mp4" type="video/mp4"></video>
```

autoplay, muted, loop속성은 따로 값 할당이 필요 없는 속성입니다. playsinline은 ios에서 자동재생을 하기 위해 필요합니다.

이제 플랫폼 전반에 걸쳐 움직이는 gif를 비디오로 재생할 수 없습니다. lazy loading을 구현하려면?

chrome은 비디오를 느리게 로드하지만 모든 브라우저에서 이러한 최적화된 동작을 제공할 수는 없습니다.

사용자와 애플리케이션 요구 사항에 따라 문제를 직접 해결해야 할 수도 있습니다.

```text
<video autoplay muted loop playsinline width="610" height="254" poster="one-does-not-simply.jpg">  <source data-src="one-does-not-simply.webm" type="video/webm">  <source data-src="one-does-not-simply.mp4" type="video/mp4"></video>
```

poster속성이 추가 되었는데 이 속성을 사용하면 video 엘리먼트의 비디오가 지연 로드 될 때까지 공간을 차지할 placeholder이미지를 지정할 수 있습니다. 앞에서 다룬 img lazy loading 예제처럼 각 source 태그의 data-src속성에 동영상 url을 넣어둡니다.

여기서 intersection observer를 기반으로 이미지 lazy loading예제와 유사한 몇가지 javascript 을 사용합니다.

```text
document.addEventListener("DOMContentLoaded", function() {  var lazyVideos = [].slice.call(document.querySelectorAll("video.lazy"));  if ("IntersectionObserver" in window) {    var lazyVideoObserver = new IntersectionObserver(function(entries, observer) {      entries.forEach(function(video) {        if (video.isIntersecting) {          for (var source in video.target.children) {            var videoSource = video.target.children[source];            if (typeof videoSource.tagName === "string" && videoSource.tagName === "SOURCE") {              videoSource.src = videoSource.dataset.src;            }          }          video.target.load();          video.target.classList.remove("lazy");          lazyVideoObserver.unobserve(video.target);        }      });    });    lazyVideos.forEach(function(lazyVideo) {      lazyVideoObserver.observe(lazyVideo);    });  }});
```

video 태그를 lazy loading할 때 모든 자식 source엘리먼트들을 반복하면서 data-src속성을 src속성에 대입합니다. 이를 완료하면 엘리먼트에서 load메서드를 호출하여 비디오 로딩을 발생시키면 autoplay속성에 의해 자동적으로 비디오가 재생됩니다.

이 방법을 사용하면 움직이는 gif대신 비디오를 사용할 수 있으면서 데이터 사용량도 줄이고 지연 로딩을 구현할 수 있게 됩니다.

#### 6. 주의 해야할 사항 <a id="LazyLoading-6.&#xC8FC;&#xC758;&#xD574;&#xC57C;&#xD560;&#xC0AC;&#xD56D;"></a>

이미지 및 비디오를 lazy loading 하는 것은 성능 이점을 가지 수도 있지만 , 잘못 이해 한다면 의도하지 않은 결과를 발생할 수 있습니다.

**1\) 폴드를 기억하라**

\(폴드 : 스크롤 없이 볼 수 있는 영역\)

javascript 를 사용하여 페이지에 있는 모든 미디어 리소스를 lazy loading하는 것이 좋을 수 있지만 이러한 부분을 한번 고려해야합니다.

스크롤 없이 볼 수 있는 폴드 영역에 있는 리소스들은 lazy loading이 되어서는 안됩니다. 이러한 resource는 중요한 점으로 간주되어야 하므로 정상적으로 로딩이 되어야 합니다.

lazy loading을 하는 대신 평범한 방식으로 중요한 resource를 로딩하는 이유는 lazy loading 스크립트가 로딩을 완료하고 실행을 시작하여 DOM이 반응하기 전까지 중요한 자원 리소스들의 lazy loading을 지연시킨다는 점입니다.

스크롤해야 볼 수 있는 부분의 이미지는 괜찮지만 폴드 영역에 위치한 중요한 resource들은 img태그를 사용하는 것이 더 빠릅니다.

물론 웹사이트들이 다양한 크기의 스크린에서 보여지고 있는 요즘은 폴드 영역이 어디에 놓여 있는지 명확하지 않습니다.

노트북에서 폴드 영역이 위에 있다면 모바일 기기에선 아래에 있을 수 있습니다. 모든 상황에서 이 문제를 최적으로 해결하기 위한 최고의 해결책은 없습니다.

페이지의 중요 리소스들을 따로 관리하여 일방적인 방식으로 로드해야 합니다.

또한 lazy load를 발생시키는 폴드 영역의 기준선은 너무 엄격하지 않아도 됩니다.

사용자가 해당 리소스가 있는 부분으로 스크롤하기 전에 이미지가 잘 로드될 수 있도록 폴드 영역 아래로 일정 거리의 버퍼 영역을 설정하는 것이 좋습니다.

예를 들어 Intersection Observer api를 사용하면 새로운 IntersectionObserver 인스턴스를 만들 때 옵션 객체에서 rootMargin속성을 지정할 수 있습니다.

이건 효과적으로 엘리먼트에 버퍼를 주며 , 엘리먼트가 화면에 표시되기 전에 지연 로딩 동작을 수행합니다.

```text
let lazyImageObserver = new IntersectionObserver(function(entries, observer) {  // Lazy loading image code goes here}, {  rootMargin: "0px 0px 256px 0px"});
```

rootMargin에 대한 값이 css의 margin속성 값과 유사하게 보이는 이유는 같은 값이 기 때문입니다. 이 경우 observer 요소의 맨 아래 여백\(기본 적으로 브라우저 뷰포트이지만 root속성을 사용하여 특정 요소로 변경할 수 있습니다.\)을 256픽셀로 확장합니다.

즉, 이미지 요소가 뷰포트에서 256픽셀 이내에 있으면 콜백함수가 실행됩니다. 즉 사용자가 실제로 보기 전에 이미지가 로드되기 시작합니다.

스크롤 이벤트를 사용하여 동일한 효과를 얻으려면 getBoundingtlientRect확인 란을 조정하여 버퍼를 포함시키면 intersection observer를 지원하지 않는 브라우저에서도 동일하게 작동합니다.

**2\) 레이아웃 및 placeholder**

lazy loading미디어는 placeholder를 사용하지 않을 경우 레이아웃을 변경시킬 수 있습니다. 이러한 변화는 사용자를 혼란스럽게 할 수 있으며 시스템 리소스를 소비하고 값 비싼 DOM 레이아웃 작업을 유발할 수 있습니다. 최소한 대상 이미지와 동일한 크기를 차지하는 단색 placeholder나

로드하기 전에 미디어 항목의 내용을 암시하는 LQIP\( [http://www.guypo.com/introducing-lqip-low-quality-image-placeholders/](http://www.guypo.com/introducing-lqip-low-quality-image-placeholders/) \) 또는 SQIP \([https://github.com/technopagan/sqip](https://github.com/technopagan/sqip) \) 와 같은 기술을 사용하는 것이 좋습니다.

img 태그에선 src 속성이 최종 이미지의 URL로 업데이트될 때까지 태그의 위치가 변경되면 안됩니다. video태그에선 이미지 placeholder를 사용하기 위해 poster속성을 사용합니다. 또한 width와 height 속성 모드 img및 video태그에서 사용할 수 있는 속성입니다.

이렇게 하면 미디어가 로드 될 때 placeholder에서 최종 이미지로 전환해도 엘리먼트의 크기가 변경되지 않습니다.

**3\) 이미지 디코딩 지연**

Javascript 에서 큰 이미지를 로딩하여 DOM에 놓으면 기본 스레드가 잠기기 때문에, 디코딩이 발생하는 동안 사용자 인터페이스가 짧은 시간동안 응답하지 않게 됩니다. DOM에 삽입하기 전에 디코드 메서드를 이용한 비동기 이미디 디코딩\([https://medium.com/dailyjs/image-loading-with-image-decode-b03652e7d2d2](https://medium.com/dailyjs/image-loading-with-image-decode-b03652e7d2d2)\)을 사용하면 이러한 문제를 해결할 수 있습니다.

하지만 아직 모든 브라우저에서 사용할 수 없으면 사용하기 전에 먼제 확인해야 합니다.

```text
var newImage = new Image();newImage.src = "my-awesome-image.jpg";if ("decode" in newImage) {  // Fancy decoding logic  newImage.decode().then(function() {    imageContainer.appendChild(newImage);  });} else {  // Regular image load  imageContainer.appendChild(newImage);}
```

\(Codepen 예제 : [https://codepen.io/malchata/pen/WzeZGW](https://codepen.io/malchata/pen/WzeZGW)\)

대부분의 이미지가 작다면 큰 효과는 없지만, 큰 이미지를 지연 로딩하여 DOM에 삽입할 때 분명 효과가 있습니다.

**4\) 로드가 되지 않을 때**

```text
var newImage = new Image();newImage.src = "my-awesome-image.jpg";newImage.onerror = function(){  // Decide what to do on error};newImage.onload = function(){  // Load the image};
```

예를 들어 5분 동안 HTML캐싱 정책이 있다고 가정 했을 때 사용자는 사이트를 방문하거나 사용자가 탭을 연 상태로 오랫동안 있다가 다시 사이트를 탐색하는 경우에 어떤 시점에 재배포가 발생한다고 할 때, 이 배포 중에 이미지 리소스의 이름이 해시 기반으로 변경이 되거나 완전히 제거된다면

사용자가 이미지를 지연 로드할 때는 리소스를 사용할 수 없으므로 오류가 발생하여 이미지가 로드되지 않고 오류가 발생합니다.

비교적 드문 케이스이지만, 지연 로딩이 실패한 경우 백업 계획을 세울 수 있습니다.

**5\) 자바스크립트의 사용 가능성**

javascript를 항상 사용할 수 있다고 가정해서는 안됩니다.

javascript를 사용할 수 없는 경우, 이미지를 지연 로딩하려 할 때 이미지를 보여주는 noscript 태그를 고려해볼 수 있습니다.

가장 간단한 대체 예제는 javascript가 비활성화된 경우 이미지를 제공하기 위해 noscript태그를 사용하는 것입니다.

```text
<!-- An image that eventually gets lazy loaded by JavaScript --><img class="lazy" src="placeholder-image.jpg" data-src="image-to-lazy-load.jpg" alt="I'm an image!"><!-- An image that is shown if JavaScript is turned off --><noscript>  <img src="image-to-lazy-load.jpg" alt="I'm an image!"></noscript>
```

javascript 를 사용할 수 없으면 위의 예제는 placeholder 이미지와 noscript태그에 포함된 이미지가 모두 표시 됩니다, 이 문제를 해결하기 위해 html태그에 no-js클래스를 다음과 같이 배치할 수 있습니다.

| `<html class="no-js">` |
| :--- |


그런 다음 javascript가 사용가능한 경우 html 엘리먼트에서 no-js클래스를 제거하는 코드를 head 태그 안에 넣습니다. 다만 스타일 시트를 요청하는 link태그 앞에 배치 합니다.

| `<script>document.documentElement.classList.remove("no-js");</script>` |
| :--- |


마지막으로 css를 사용하여 javascript를 사용할 수 없을 때 lazy loading에 사용하는 클래스로 엘리먼트를 숨길 수 있습니다.

| `.no-js .lazy { display: none;}` |
| :--- |


이렇게 하면 placeholder이미지가 로드 되지 않지만 결과가 더 바람직합니다. javascript를 사용할 수 없는 사용자는 placeholder이미지를 볼 순 없지만 실제 이미지를 볼 수 있습니다.

#### 7. 참고 사이트 <a id="LazyLoading-7.&#xCC38;&#xACE0;&#xC0AC;&#xC774;&#xD2B8;"></a>

아래의 사이트들에서 의역한 내용을 바탕으로 해당 글을 작성 하였습니다.

\(완료\) [https://blog.stackpath.com/glossary/lazy-loading/](https://blog.stackpath.com/glossary/lazy-loading/)

\(완료\) [https://developers.google.com/web/fundamentals/performance/lazy-loading-guidance/images-and-video/](https://developers.google.com/web/fundamentals/performance/lazy-loading-guidance/images-and-video/)​

\(완료\) [https://www.sitepoint.com/five-techniques-lazy-load-images-website-performance/](https://www.sitepoint.com/five-techniques-lazy-load-images-website-performance/)​

