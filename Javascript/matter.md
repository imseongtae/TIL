# Matter


## Table of Contents


---


## 배열에서 중복된 요소를 묶어서 다시 배열로 꺼내는 예제

```js
const arr = [1, 2, 3, 4, 5, 6, 7, 1, 3, 5, 6, 2, 7, 1, 4, 4, 100, 20, 4];
console.log(arr);

function getMap(arr) {
  let resultMap = {};
  for (let i in arr) {
    // console.log(arr[i]);
    if (!(arr[i] in resultMap)) {
      resultMap[arr[i]] = [];
    }
    resultMap[arr[i]].push(arr[i]);
  }
  return resultMap;
}

// getMap(arr);
console.log(getMap(arr));
```