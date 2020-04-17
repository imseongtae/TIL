# Axios

## What is the axios

Axios는 간편한 HTTP 라이브러리로 기타 jQuery의 $ajax나 Angular의 HTTP 모듈에 비해 이용하기 편리하다. 기본적으로 `Promise`를 사용하며, 비동기 작업을 효과적으로 처리할 수 있도록 `async/await`를 지원한다. Vue 2.0 버전 이전에는 공식적인 HTTP 라이브러리로 vue-resource를 이용했지만 Vue 2.0 버전부터 axios를 주로 사용한다

혹자의 말에 의하면 Vue.js를 만든 에반 유조차 Axios를 공식적으로 언급할 정도니 현재는 Axios가 대세인 것은 확실하다. Axios의 설치는 https://github.com/axios/axios#installing 에 명시된 대로 npm이나 bower 그리고 CDN을 이용해 다음과 같이 설치할 수 있다.

### 설치

```
npm install axios
bower install axios 
CDN - script in browser
```

## 간단한 axios 예제

간단한 예제 제작 후 axios에 대해 알아보기

axios를 이용해서 데이터를 요청하면 JSON 형태의 데이터를 반환하는 서버가 필요하다. 여기서는 [`https://api.adviceslip.com/`](https://api.adviceslip.com/)에서 좋은 문장을 간단한 JSON 형태로 제공하므로 이를 이용하기로 한다. 데이터 요청 URL은 [`https://api.adviceslip.com/advice`](https://api.adviceslip.com/advice)이며 브라우저 URL에 입력하고 접속하면 다음과 같이 JSON 형태의 데이터를 반환한다.

```json
{
	"slip": {
		"advice":"Always block trolls.",
		"slip_id":"12"
	}
}
```

### CDN을 이용한 방법

- `created()`와 `axios.get()` 메서드를 이용해 설정할 데이터를 가져옴
- index.html

### JSON-Server를 이용한 방법

`json-server`를 설치하면 [`http://localhost:3000/`](http://localhost:3000/slip)으로 JSON Server를 띄울 수 있고, 이 서버에 axios의 메서드를 수행해볼 수 있다.

- **json-server 설치**

  ```bash
    $ npm install -g json-server
  ```

- **json-server 서버 실행**

  ```bash
    $ json-server --watch data.json
  ```

- **json-server 서버가 조회할 더미 데이터**

  ```
    {
    	"slip": [
    		{
    			"advice":"If you're feeling tired or anxious, a pint of water will almost always make you feel better.",
    			"slip_id":"13"
    		},
    		{"advice":"Just because you are offended, doesn't mean you are right.","slip_id":"79"},
    		{"advice":"Never buy cheap cling film.","slip_id":"25"}
    	],
    	"slip1": {"advice":"Just because you are offended, doesn't mean you are right.","slip_id":"79"},
    	"slip2": {"advice":"Never buy cheap cling film.","slip_id":"25"}
    }
  ```

- `index.html` 예시파일

  ```vue
  <div id="app">
    <ul>
      <li v-for="slip in slips" :key="slip.slip_id">
      	<div>number: {{slip.slip_id}} | {{slip.advice}}</div>
  
      </li>
    </ul>
  </div>
      
  <script src="<https://cdn.jsdelivr.net/npm/vue/dist/vue.js>"></script>
  <script src="<https://unpkg.com/axios/dist/axios.min.js>"></script>
  <script>
    new Vue({
      el:'#app',
      data() {
      	return {
     			slips: []
      	}
      },
      created() {
      	axios.get('<http://localhost:3000/slip>')
      	.then((res) => {
  	    	console.log(res)
      		this.slips = res.data
      	})
  	    .catch(err => {
    	  	console.error(err)
      	})
      }
    })
  </script>
  ```

## axios 메서드

### GET request

axios에서 GET 요청은 하나의 자원이나 다수의 자원을 검색하기 위해 서버에 요청하는 것이며 다음과 같은 형식을 사용한다.

- example

  ```
    axios.get(url, [, config]).then((response) => {  }).catch((error => { }))
    axios.get(config).then((response) => { }).catch((error) => { })
  ```

**URL 파라미터는 자원의 위치**를 나타낸다. **선택적으로 사용할 수 있는 config 파라미터는 get, post, put 같은 메서드를 설정하는 데 사용**한다. method, url, 특정 자원을 검색하는 데 사용하는 params 같은 프로퍼티로 다음과 같이 구성될 수 있다.

### POST request

POST 요청은 하나의 자원이나 다수의 자원을 생성하도록 서버에 요청하는 것으로 다음의 형식을 따른다.

### PUT request

PUT 요청은 특정 자원을 수정하거나 대체하도록 서버에 요청하는 것으로 다음의 형식을 따른다.

### DELETE request

DELETE 요청은 특정 자원을 삭제하도록 서버에 요청하는 것으로 다음의 형식을 따른다.