# 💬 Git

### 커밋 메세지 규칙

1. 제목과 본문을 한 줄 띄어 구분
2. 제목은 50자 이내
3. 제목 첫 글자는 대문자
4. 제목 끝에 마침표 X
5. 제목은 명령문으로, 과거형 X
6. 본문의 각 행은 72자 이내 (줄바꿈 사용)
7. 본문은 어떻게 보다 무엇을, 왜에 대하여 설명

### 커밋 메세지 구조

```
<type>(<scope>): <subject>          -- 헤더(essential)
<BLANK LINE>
<body>                              -- 본문(optional)
<BLANK LINE>
<footer>                            -- 바닥글(optional)
```

* type
  * `build` : 빌드 관련 파일 수정
  * `feat`: 새로운 기능 추가, 기존의 기능을 수정
  * `fix`: 기능 버그 수정
  * `chore` : 패키지 매니저, 그 외 빌드와 관련없는 파일(.gitignore) 수정
  * `ci` : CI관련 설정 수정
  * `docs` : 문서, 주석 수정
  * `style` : 코드 스타일 혹은 포맷 등
  * `refactor` : 코드 리팩토링
  * `test` : 테스트 코드 수정
  * `release`: 특정 버전 릴리즈
* footer: 아래 명령어를 통해 이슈를 닫을 수 있다.
  * `close`
  * `closes`
  * `closed`
  * `fix`
  * `fixes`
  * `fixed`
  * `resolve`
  * `resolves`
  * `resolved`

### 출처

* [https://meetup.nhncloud.com/posts/106](https://meetup.nhncloud.com/posts/106)
* [https://udacity.github.io/git-styleguide/](https://udacity.github.io/git-styleguide/)
* [https://docs.github.com/en/issues/tracking-your-work-with-issues/linking-a-pull-request-to-an-issue](https://docs.github.com/en/issues/tracking-your-work-with-issues/linking-a-pull-request-to-an-issue)
