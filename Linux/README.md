# Linux



## Table of Contents

1. [자주 쓰는 명령어](#자주-쓰는-명령어)
1. [vi Editor](#vi-Editor)

---



## 자주 쓰는 명령어

| 명령어                 | 설명                                                  |
| ---------------------- | ----------------------------------------------------- |
| ls                     | 파일 및 폴더 목록                                     |
| cd                     | 디렉토리 이동                                         |
| pwd                    | 현재 폴더까지의 경로 표현                             |
| mkdir                  | 디렉토리 생성                                         |
| rm <filename>          | <filename> 파일을 삭제                                |
| rm *.<확장자명>        | rm *.dat 의 경우 '.dat' 확장자 파일을 모두 삭제       |
| rm *                   | 모든 파일 삭제                                        |
| rmdir <directoryname>/ | <directoryname> 디렉토리를 삭제                       |
| rm -r <directoryname>/ | `-r`명령어를 붙이면 파일이 들어있더라도 디렉토리 삭제 |



### rm 예시

**1. 파일 삭제**

```bash
rm README.md 
```

**2. 디렉토리/폴더 삭제**

```bash
rmdir node_modules/
```

**3. node_modules 폴더의 파일들까지 함께 삭제**

```bash
rm -r node_modules/ # rmdir과는 달리 파일이 있어도 삭제
```

**4. 모든 파일 삭제**

```
rm *
```





## vi Editor 

### git을 능숙하게 다루려면 vi Editor 사용법에 대한 이해가 조금 필요하다!

`git shortlog`처럼 로그 메시지를 보는 명령어를 입력하면 :(콜론)을 출력한 상태에서 사용자 입력을 기다린다.  
커밋 히스토리는 무제한적으로 늘어날 수 있기 때문에 사용자의 입력을 통해서 중단할지 아니면 계속해서 보여줄지를 결정해야 하는데, `q` 를 누르면 git log 명령은 중지된다. 

| 명령어          | 설명                                              |
| --------------- | ------------------------------------------------- |
| `vi <filename>` | 파일의 편집                                       |
| `i`             | 데이터 입력                                       |
| `esc`           | 작성이 다되면 esc키를 누른다                      |
| `:wq`           | esc 이후 `:`을 누른후 write quit, 파일을 빠져나감 |
| `q!`            | 강제로 파일을 나올때                              |
| `cat`           | 파일의 내용 확인                                  |
| `--help`        | 세부 옵션 확인                                    |

**[⬆ back to top](#table-of-contents)**





## 참고 문헌

- [리눅스 기본 명령어]([https://gyoogle.dev/blog/linux/Linux%20Basic%20Command.html](https://gyoogle.dev/blog/linux/Linux Basic Command.html))
- [리눅스 rm 명령어, 옵션 사용법 정리 (파일, 디렉토리 삭제 명령)](https://withcoding.com/95)