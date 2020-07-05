# Big-O

자바스크립트로 하는 자료구조와 알고리즘을 보며 학습한 자료

- [교재 정오표](http://acornpub.co.kr/book/javascript-data-algorithms#errata)



## Big-O

빅오 표기법은 알고리즘 최악의 경우 복잡도를 측정한다. 빅오 표기법에서 n은 입력의 개수를 나타낸다. 빅오와 관련된 질문으로 "n이 무한으로 접근할 때 무슨 일이 일어날까?"가 있다. 

알고리즘을 구현할 때 **빅오 표기법**은 해당 알고리즘이 얼마나 효율적인지 나타내기 때문에 빅오 표기법은 중요하다.

### O(1)

배열에 있는 항목을 인덱스를 사용해 접근하는 경우가 O(1) 알고리즘의 예다. 

```js
function exampleLinear(n) {
  for (let i = 0; i < n; i++) {
    console.log(i);
  }
}

exampleLinear(3);

```

```bash
1
2
3
```



## O(n<sup>2</sup>)

O(n<sup>2</sup>) 2차 시간이며, 2차 시간 복잡도는 다음과 같다.

```js
function exampleQuadratic(n) {
  for (let i = 0; i < n; i++) {
    console.log(i)
    for (let j = i; j < n; j++) {
      console.log(j);    
    }    
  }
}
exampleQuadratic(3)
```

- 출력 결과

```bash
0
0
1
2
1
1
2
2
2
```





## O(n<sup>3</sup>)

O(n<sup>3</sup>) 3차 시간이며, 3차 시간 복잡도는 다음과 같다.

- 3번째 for문의 값이 `let k = j; k < n; k++` 가 맞는지 모르겠다. 정오표에 나오지 않음..! 책의 예제를 따르면 무한 반복이 됨..

```js
function exampleCubic(n) {
  for (let i = 0; i < n; i++) {
    console.log(i)
    for (let j = i; j < n; j++) {
      console.log(j);
      for (let k = j; k < n; k++) {
        console.log(k);
      }
    }    
  }
}

exampleCubic(3);
```

- 출력 결과

```bash
0
0
0
1
2
1
1
2
2
2
1
1
1
2
2
2
2
2
2
```



