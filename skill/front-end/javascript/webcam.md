---
description: 모바일 웹 카메라 기능을 사용하기 위해 사용하고자합니다.
---

# 📷 WebCam

### 요약





### 이슈 로그

1.  Native 카메라는 전면이 좌우반전으로 출력되지만, 모바일 웹 카메라는 후면이 좌우반전 출력

    \-> 후면 video tag를 좌우반전

```
<style>
	video{
    	    transform: rotateY(180deg);
            -moz-transform:rotateY(180deg); /* Firefox */
            -webkit-transform:rotateY(180deg); /* Safari and Chrome */
	}
</style>
```

####

#### \[출처]

[https://developer.mozilla.org/en-US/docs/Web/API/Media\_Capture\_and\_Streams\_API](https://developer.mozilla.org/en-US/docs/Web/API/Media\_Capture\_and\_Streams\_API)
