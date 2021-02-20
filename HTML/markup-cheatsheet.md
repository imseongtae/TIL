# HTML Cheat Sheet


## table of contents
- [paragraph](#paragraph)
- [init list stlye](#init-list-stlye)

## paragraph

`pre-wrap`: 연속 공백 유지. 줄 바꿈은 개행 문자와 <br> 요소에서 일어나며, 한 줄이 너무 길어서 넘칠 경우 자동으로 줄을 바꿉니다
`break-word`: 실제 overflow-wrap 속성에 상관하지 않고, word-break: normal과 overflow-wrap: anywhere를 설정한 것과 같은 효과를 냅니다

```css
.word {
  white-space: pre-wrap;
  word-break: break-word;
}
```

출처  
- [https://developer.mozilla.org/ko/docs/Web/CSS/white-space](#https://developer.mozilla.org/ko/docs/Web/CSS/white-space)

## init list stlye
- reset.css에 의해 초기화된 li style을 해제하는 속성

```css
li {            
  list-style: disc inside none;
  display: list-item;
  margin-left: 1rem;
}
```
