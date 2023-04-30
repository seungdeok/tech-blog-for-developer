# Editorconfig 도입

## Editorconfig란 무엇인가?

코딩 스타일을 정의하기 위한 **파일 형식 +** 텍스트 편집기 플러그인 **컬렉션**

다양한 편집기와 IDE에서 동일한 프로젝트를 작업하는 개발자들의 일관된 코딩 스타일을 유지



## 어떻게 생겼나?

```
# react 예시 (.editorconfig)
# https://editorconfig.org
root = true

[*]
charset = utf-8
end_of_line = lf
indent_size = 2
indent_style = space
insert_final_newline = true
max_line_length = 80
trim_trailing_whitespace = true

[*.md]
max_line_length = 0
trim_trailing_whitespace = false

[COMMIT_EDITMSG]
max_line_length = 0
```



## 파일 형식과 속성

### 파일 형식

| 형식             | 설명                              |
| -------------- | ------------------------------- |
| `*`            | `/`경로 구분 기호( ) 를 제외한 모든 문자열과 일치 |
| `**`           | 모든 문자열과 일치                      |
| `?`            | 단일 문자와 일치                       |
| `[name]`       | _이름_ 의 모든 단일 문자와 일치             |
| `[!name]`      | _이름_ 에 없는 단일 문자와 일치             |
| `{s1,s2,s3}`   | 주어진 문자열과 일치(쉼표로 구분)             |
| `{num1..num2}` | _num1_ 과 _num2_ 사이의 모든 정수와 일치   |



### 속성

| 속성                         | 설명                                                        |
| -------------------------- | --------------------------------------------------------- |
| `indent_style`             | `tab`, `space`                                            |
| `indent_size`              | 열 수와 소프트 탭의 너비(지원되는 경우)를 정의하는 정수(지정하면 `tab_width`로 사용됨)   |
| `tab_width`                | 탭 문자를 나타내는 데 사용되는 열 숫자를 정의(**`indent_size`이 있으면 생략)**     |
| `end_of_line`              | 줄바꿈 표시 방법을 제어(`lf`, `cr`, `crlf`)                         |
| `charset`                  | `latin1` , `utf-8` , `utf-8-bom` , `utf-16be` ,`utf-16le` |
| `trim_trailing_whitespace` | 줄 바꿈 문자 앞에 있는 공백 문자 제거 여부를 `true`, `false`                |
| `insert_final_newline`     | 저장할 때 파일이 줄바꿈으로 끝날지 여부를 `true`, `false`                   |
| `root`                     | (필수값) `true` 값일 때 파일 검색 중단                                |



## 출처

* [https://editorconfig.org/](https://editorconfig.org/)
