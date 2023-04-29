---
description: 모바일 웹 카메라 기능을 사용하기 위해 사용하고자합니다.
---

# 📷 \[JS] WebCam 카메라 좌우반전

### 기존 로직

* MediaStream API를 활용하여 web browser에서 카메라 기능 구현



### 문제점

* Native 카메라는 전면이 좌우반전으로 출력되지만, 모바일 웹 카메라는 후면이 좌우반전 출력



### 변경된 로직

* user-agent 활용하여 mobile로 접근한 경우 체크

```javascript
/*
    Mozilla (Gecko, Firefox): Mobile
    WebKit-based (Android, Safari): Mobile
    Blink-based (Chromium, Google Chrome, Opera 15+): Mobile
    Presto-based (Opera 12-): Mobi
*/

const isMobilePlatform = () => {
    const { userAgent } = navigator
    return userAgent.indexOf('Mobi') > -1;
}

```



* 후면 video tag를 좌우반전

```css
<style>
	video{
    	    transform: rotateY(180deg);
            -moz-transform:rotateY(180deg); /* Firefox */
            -webkit-transform:rotateY(180deg); /* Safari and Chrome */
	}
</style>
```

####

### 출처

* [https://developer.mozilla.org/en-US/docs/Web/API/Media\_Capture\_and\_Streams\_API](https://developer.mozilla.org/en-US/docs/Web/API/Media\_Capture\_and\_Streams\_API)
* [https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/User-Agent](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/User-Agent)
