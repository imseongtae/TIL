# Error

학습하며 만났던 Git Error 정리



## LF will be replaced by CRLF in git

### 원인: **운영체제 차이**로 인해 발생하는 문제!

- LF will be replaced by CRLF in git - What is that and is it important? [duplicate]

```bash
warning: LF will be replaced by CRLF in first-data-parsing/add_to_sheet.js. The file will have its original line endings in your working directory
```



### 해결 방법

유닉스 / 리눅스 계열은 **LF**로 개행 문자를 사용하고, 윈도우는 **CRLF** 형식으로 개행 문자를 사용한다

- 이럴 땐 `core.autocrlf` 값을 `true`로 설정하면 올릴 때 알아서 처리해준다

```bash
$ git config core.autocrlf true
```

