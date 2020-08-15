# Table
table 태그를 사용할 때 같이 사용되는 caption, colgroup, scope 등의 활용을 정리

## table of contents
- [Table 예시1](#Table-예시1)
- [Table 예시2](#Table-예시2)


---

## Table 예시1
- `caption` 의 사용
- `colgroup`, `col` 의 사용
- `th`의 `scope` 속성 사용

```html
<!-- 기본구조의 요소를 모두 갖추어야 한다. 그룹핑을 한다면 바디가 필수적으로 있어야 하고, 부가적으로 헤드, 풋이 있어야 한다. -->
<table border width="100%" height="30%">
  <caption>table caption</caption>
  <!-- 칸마다 크기를 지정하고 싶을 떄 colgroup을 사용한다 -->
  <colgroup>
    <col width="50">
    <!-- 크기를 줄 때 중요한 건 모든 요소에(4개 전부) 지정하지 않는다. 왜냐하면 브라우저마다 한칸의 크기가 보더를 포함하는 경우, 아닌 경우가 있으므로 하나를 뺴고 해야 브라우저마다 호환성이 높아진다.  -->
    <col>
    <col>
    <col>
  </colgroup>
  <thead>
    <tr>
      <!-- th를 사용할때는 꼭 scope로 범위를 정해야 한다. 제목을 통해 셀들의 범위를 정해야 한다. -->
      <!-- scope | row | colgroup | rowgroup -->
      <th scope="col">table header cell</th> <!-- col을 통해서 이 제목이 나타내는 방향을 나타낸다. 열 방향이라는 것을 표시-->
      <th scope="col">table header cell</th>
      <th scope="col">table header cell</th>
      <th scope="col">table header cell</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="3">table data cell</td>
      <td>table data cell</td>
      <td>table data cell</td>
      <td>table data cell</td>
    </tr>
    <tr>
      <!-- <td>table data cell</td> -->
      <td>table data cell</td>
      <td>table data cell</td>
      <td>table data cell</td>
    </tr>
    <tr>
      <!-- <td>table data cell</td> -->
      <td>table data cell</td>
      <td>table data cell</td>
      <td>table data cell</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <th scope="rowgroup">data,result of col</th> <!-- row 방향의 범위를 나타낸다.-->
      <td colspan="3">...</td> <!-- 컬럼 3개를 합친다는 개념 -->
      <!-- <td>result</td> -->
      <!-- <td>result</td> -->
    </tr>
  </tfoot>
</table>
<!-- //table -->
```


## Table 예시2
- `rowspan`을 활용한 테이블 예시

```html
<table>
  <tr>
    <th>Name</th>
    <td>Jill Smith</td>
  </tr>
  <tr>
    <th rowspan="2">Phone</th>
    <td>555-77854</td>
  </tr>
  <tr>
    <td>555-77854</td>
  </tr>
</table>
```



## 참고 자료

- [웹접근성table의-scopecol과-scoperow](https://jowook.tistory.com/entry/%EC%9B%B9%EC%A0%91%EA%B7%BC%EC%84%B1table%EC%9D%98-scopecol%EA%B3%BC-scoperow)