# Signed/Unsigned

## Spoiler(미리 보기)

본격적으로 내용을 정리하기에 앞서 **Signed/Unsigned의 차이**는 **음수를 표현 하느냐 안 하느냐**의 차이이다. 이 차이로 인로 인해 메모리에 비트(bit)를 기록하는 방식이 달라진다.

- 아래 그림은 **정수 3인 1바이트**를  2진수로 표현할 때 할당되는 메모리 비트

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6b163100-1b0e-4df3-9676-05aa7332ee22/diff.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6b163100-1b0e-4df3-9676-05aa7332ee22/diff.png)

## Signed

### Signed 개념

- **부호를 가지는 값**(양수, 음수를 구별)
- Signed Char의 범위: -128 ~ 127
- Signed 에 대한 wikipedia 설명
  - signed는 C/C++ 프로그램 언어에서 정수형 변수 중 부호를 갖는 변수를 선언 한다. 정수형 중 음수는 2의 보수 체계를 사용하므로 이 키워드에 의해 부호를 사용할 수 있도록 변수 선언할 수 있다. 그러나 정수형의 변수에서 unsigned가 없으면 음수를 사용할 수 있는 부호를 갖는 정수형이 된다. 따라서 프로그램에서는 이 키워드는 많이 사용은 하지 않는다.
- Signed에서는 파란색으로 칠해진 영역이 MSB

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/71b65f1a-8f6d-435b-ac1d-8920bc2e8224/Signed.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/71b65f1a-8f6d-435b-ac1d-8920bc2e8224/Signed.png)

## Unsigned

### Unsigned 개념

- **부호를 가지지 않는 값**(양수만 표현)
- Unsigned Char의 범위 : 0~255
- Unsigned에 대한 wikipedia 설명
  - unsigned는 C/C++ 언어에서 사용되는 지정자로 정수형과 같이 사용되어 부호 비트를 제거해 저장 가능한 양수 범위를 두배로 늘이는 역할을 한다. char와 int의 signed 정수형 변수에서 MSB가 부호 비트이다. 1이면 음수이고 0이면 양수이다. 그러나 unsigned을 사용하면 음수를 사용하지 않겠다는 의미 이므로 부호 비트가 필요 없다. 따라서 이진수와 같은 십진수가 된다.
- Unsigned에서는 MSB가 없음

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/247dfd0e-4040-40c6-9901-6a27c026d063/Unsigned.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/247dfd0e-4040-40c6-9901-6a27c026d063/Unsigned.png)

## JavaScript의 숫자

JavaScript는 태생적으로 **정확한 수 계산**을 위해서 만들어진 언어가 아니다. 그래서 숫자에 대해 **정밀하고, 범용성이 높은 규격**을 선택했다!

JavaScript는 **IEEE 754**(ITripleE 754)라는 규격을 따르고 있다. JavaScript의 숫자는 IEEE 754로 규정된 64비트 부동소수점이며, 64비트라는 크기로 인해 **정밀한 값을 표현**하는데 좋다. 그렇지만 여기서 **정밀하다는 것은 정확하다는 뜻이 아니다**.

- 아래 그림은 자바스크립트에서 사용하는 **IEEE 754 부동소수점 규격**

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/86d39678-d517-4aa4-bfce-44912f1fed68/IEEE754.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/86d39678-d517-4aa4-bfce-44912f1fed68/IEEE754.png)

### JavaScript의 숫자를 이해하기 위한 예시

- 1.0과 1은 다르다. 1.0은 1에 아주 근사(근접)한 수이다.
- 자바스크립트의 숫자 규격은 스탑 워치⏱️로 비유할 수 있다. 스탑 워치⏱️는 1000분의 1초까지 정밀하게 계산하지만 **이 범위를 벗어난다면 오차를 허용**한다.

### JavaScript의 숫자의 특징

- JavaScript는 **정밀한 값을 표현**하는데 좋은 규격을 따름
- **IEEE 754 부동소수점 규격**은 `Number` 타입으로 `Double`로 취급

## Signed/Unsigned와 JavaScript의 관계?

### 무슨 관계가 있을까?

- 자바스크립트에서 **버퍼를 읽거나 쓰는 예문**들을 볼때 C에서 사용되는 `signed`와 `unsigned`라는 키워드에 비유하는 내용을 자주 접할 수 있음

- 자바스크립트 비트연산자 사용시 Unsigned 32-bit Integer로 변환

- `unsigned/signed`에 따라서 **성능에 영향**을 줄 때 ⇒ 64-bit signed 대신 32-bit unsigned를 사용할때 성능이 빠르고 이게 병목지점인 경우

- `unsigned`를 사용하기 위해 결정내리는 경우(libsora님 글)
1. API에서 unsigned를 사용하라는 경우
  2. 2진수, 16진수가 개입된 로직
  3. 이외에 나머지 경우는 전부 signed

## 참고문헌

- [변수](https://tew_books.gitlab.io/javascript_tutorial/2.Variables.html)
- [나는 unsigned가 싫어요](https://libsora.so/posts/i-hate-unsigned/)
- [Signed와 Unsigned 차이 - Firejune](https://firejune.com/1791/Signed와+Unsigned+차이)
- [Signed와 Unsigned의 차이.](https://themangs.tistory.com/entry/Signed와-Unsigned의-차이)
- [자바스크립트 (JavaScript)에서 Unsigned 32-bit Integer로 변환하기](https://devday.tistory.com/entry/자바스크립트-JavaScript에서-Unsigned-32bit-Integer로-변환하기)
- 모던 자바스크립트 입문 - 부동소수점과 정확도 문제
- My Blog

