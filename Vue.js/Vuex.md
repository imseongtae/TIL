# Vuex

## What is the Vuex?

### 효율적인 데이터 관리를 위한 Vuex 

Vuex 는 Vue.js 애플리케이션을 위한 **상태관리 패턴 라이브러리**이다. 중앙에 **데이터 저장소**를 두고 애플리케이션 내의 모든 컴포넌트들이 이용하게 한다. 많은 수의 컴포넌트로 구성된 애플리케이션의 경우 컴포넌트 간의 데이터 전달이 복잡해진다. 매번 props, eventbus 등을 이용해 데이터를 처리한다면 동적 처리가 복잡해지므로 **Vuex를 애용해 한 곳에서 데이터를 관리하고, 이 데이터를 수정 및 삭제하는 등의 작업을 수행하는 것이 효과적**이다.

`Vuex`는 **단일 상태 트리**를 사용한다. 즉, 이 단일 객체는 **모든 애플리케이션의 원본 소스 역할**을 한다. **상태가 변경되면** 하위의 Vue 컴포넌트들을 **새로 렌더링**해준다.

### Vuex를 이용해한 state 변경법

간단히 정리하면 다음 2가지 방법으로 Vuex를 이용해 state를 변경할 수 있다

- `mutation`을 이용한 직접 변경
- `action` ⇒ `mutation`을 이용한 간접 변경(비동기적 처리 가능)

1. Vuex 설치
2. Vuex  동작 이해
3. state에서 데이터를 가져오는 함수 getters
4. 상태를 바꾸는 mutation
5. 상태를 간접적으로 변경하며, 비동기적으로 동작하는 Action
6. Vuex의 보조함수
7. Mutations와 Actions의 차이점

---



## Vuex 패키지 설치

- 1단계: `vuex` 설치
- 2단계: `store.js` 파일을 생성하고, `vuex` 관련 데이터를 정의한다.
- 3단계: `main.js` 에 `vuex`를 컴포넌트들이 사용할 수 있도록 한다.

```bash
npm install vuex --save
```



어느 컴포넌트에서나 접근이 가능하도록 저장소를 만드려면 `src/store/store.js` 경로로 파일을 생성한다. 

- `strict: true`: Vuex의 상태가 mutation 핸들러 밖에서 변할 때 에러를 나타내며, 모든 상태 변화(`state mutation`)를 명확하게 트래킹한다.
- `state`: 애플리케이션에서 사용할 데이터를 포함하는 객체. Vuex는 이러한 트리 구조 형태를 취하는 하나의 상태를 사용한다. 



## 3. Getters

**상태에서 데이터를 가져오는 함수**를 나타낸다. `Getters`는 `store`에 있는 `computed` 프로퍼티로 생각할 수도 있는데, 그 이유는 `Getters`는 `computed` 프로퍼티와 비슷하게 `getter`의 결과가 **의존성(dependencies)에 기반해 캐시되기 때문**이다. 다시 말해 **의존성**에 변화가 생겼을 때만 재평가된다.

`Getters`는 때때로 컬렉션 형태의 데이터를 필터링하거나 데이터의 수를 `Vuex`로 정의된 스토어(store)의 상태에 기반해 계산할 때 사용하며, getters 블록내의 함수 정의 방법은 다음과 같다.

### getter 함수 정의법

```
function_name: (state) => {
	// Code
}
```

## 4. Mutations

**Mutation은 상태를 바꾸는 유일한 방법**으로 `mutation`을 커밋(commit)해 변경할 수 있다. `mutation`으로 **상태가 변경되는 것을 추적할 수 있으며 한 곳에서 상태를 변경하므로 일관되게 데이터를 관리**할 수 있다. `mutation`을 적용하는 방법은 다음과 같이 2단계로 나눌 수 있다.

### mutation 적용 단계

- 1단계: `store.js`에서 `mutation`을 정의
- 2단계: 컴포넌트의 해당 메서드 부분에서 커밋(commit)

여기서 커밋(`commit`)한다는 의미는 쉽게 이야기해서 '적용한다'라고 생각해도 되고, 데이터베이스에서의 커밋의 의미로 이해해도 된다. 차례대로

## 5. Actions

**Action은 `mutation`을 커밋해 간접적으로 상태를 수정할 수 있으며 비동기적으로 동작**한다.

예를 들어 파일을 읽고 쓰거나 HTTP를 요청하고 이에 대한 응답 처리과정을 생각해보면, 먼저 상당히 큰 파일의 경우 해당 작업이 언제 끝날지 알 수 없고, HTTP 요청에 대한 응답 역시 마찬가지다. 이같은 경우 동기적 처리는 해당 작업들이 완료될 때까지 기다려야 하지만 비동기적 처리는 해당 작업이 완료되면 반영하는 형태로 처리하면 되므로 기다리지 않고 다른 작업을 처리할 수 있다. 따라서 비동기적인 처리가 필요한 경우에는 이를 지원하는 action을 이용하면 된다.

### Action 적용단계

- 1단계: `store.js`에서 `action`을 정의

- 2단계: 컴포넌트의 해당 메서드 부분에서 `dispatch`

- 먼저 순서대로 actions 블록 내의 action을 정의하려면 mutations 블록 내의 mutation을 다음과 같이 작성한다.

  ```
    method_name: context => {
    	context.commit('method_name');
    }
  ```

`action`은 위와 같이 하나의 `context`를 받는 데, 이 `context`는 저장소 인스턴스의 메서드들과 프로퍼티들을 나타내며, `context.commit('method_name')`을 이용해 `'method_name'`을 커밋한다.

- 해당 메서드가 정의된 곳에서 다음과 같이 코드를 작성한다.

  ```
    method_name() {
    	this.$store.dispatch('method_name'),
    }
  ```

  위에서 `dispatch()` 메서드는 `action`을 호출하기 위한 메서드로 컴포넌트에서 해당 메서드가 호출되면 `store.js`에 정의된 `actions` 내의 `method_name`이 실행된다.



```javascript
import Vue from 'vue'
import Vuex from 'vuex'

Vue.use(Vuex)

export default new Vuex.Store({
  strict: true,
  state: {
    items: [
      {country: "France", city: "Paris", attraction: '에펠탑', entrance_fee: 10},
      {country: "Italy", city: "Venezia", attraction: '산마르코 대성당', entrance_fee: 0},
      {country: "Austria", city: "Salzburg", attraction: '호엔짤쯔부르크성', entrance_fee: 15.20},
      {country: "Germany", city: "Salzburg", attraction: '뢰머광장', entrance_fee: 0},
      {country: "Neterland", city: "Salzburg", attraction: '국립미술관', entrance_fee: 17.50},
    ],
    selectedCountry: ' ',
  }, //state
  
  getters: {
    items: state => {
      return state.items
    },
    filteredItems: state => {
      return state.items.filter(item => {
        return item.country == state.selectedCountry
      })
    }
  },
  mutations: {
    reducePrice: state => {
      state.items.forEach(item => {
        item.entrance_fee = (item.entrance_fee - (item.entrance_fee * 0.2))
      })
    },
    // reducePrice: state => {
    //   setTimeout(() => {
    //     state.items.forEach(item => {
    //       item.entrance_fee = (item.entrance_fee - (item.entrance_fee * 0.2))
    //     })        
    //   }, 4000);
    // },

    goCountry: (state, inCountry) => {
      state.selectedCountry = inCountry;
    }
  },
  actions: {
    // reducePrice: context => {
    //   context.commit('reducePrice')
    // },
    // goCountry: (context, inCountry) => {
    //   context.commit('goCountry', inCountry)
    // }
    reducePrice: context => {
      setTimeout(() => {
        context.commit('reducePrice')
      }, 4000);
    }
  },

})
```



`main.js`에서 모든 컴포넌트가 vuex를 사용할 수 있도록 추가

```javascript
import Vue from 'vue'
import App from './App.vue'
import store from './store/store'

Vue.use('Vuex')
Vue.config.productionTip = false

new Vue({
  render: h => h(App),
  store
}).$mount('#app')

```

### App.vue

```vue
<template>
  <div id="app">
    <travel-list></travel-list>
  </div>
</template>

<script>
import TravelList from './components/TravelList.vue'

export default {
  name: 'App',
  components: {
    TravelList,
    
  }
}


</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

```



### TravelList.vue

```vue
<template>
  <div id="travel-list">    
    <h2>유럽 여행</h2>
    <ul>
      <li v-for="item in items" :key="item.attraction" @click="goCountry(item.country)">
        <span>국가: {{item.country}}</span><br>
        <span>도시: {{item.city}}</span><br>
        <span>명소: {{item.attraction}}</span><br>
        <span>요금: {{item.entrance_fee}}</span>
      </li>
    </ul>
    <button @click="reducePrice" class="btn">특별 입장료 할인</button>
    <travellist-details></travellist-details>
  </div>
</template>

<script>
import TravelListDetails from './TravelListDetails.vue'
import {mapActions} from 'vuex'
// import {mapMutations} from 'vuex'

export default {
  components: {
    'travellist-details':TravelListDetails,
  },
  methods: {
    ...mapActions(['reducePrice']),
    ...mapActions(['goCountry']),
    // ...mapMutations(['reducePrice']),
    // ...mapMutations(['goCountry']),

    // goCountry(inValue) {
    //   // this.$store.state.selectedCountry = inValue;
    //   // this.$store.commit('goCountry', inValue)
    //   this.$store.dispatch('goCountry', inValue)
    // },
    // reducePrice() {
    //   // this.$store.commit('reducePrice');
    //   this.$store.dispatch('reducePrice')
    // }
  },
  filters: {
    currency(value) {
      return new Intl.NumberFormat("de-DE", {style: 'currency', currency: 'EUR'}).format(value)      
    }
  },
  computed: {
    items() {
      return this.$store.getters.items
    }
  }

}
</script>

<style scoped>
#travel-list {
  color: white;
  background-color: blue;
  padding: 10px 20px;  
}
#travel-list ul {
  padding: 0;
  list-style-type: none;
}
#travel-list li {
  margin: 10px;
  padding: 20px;
  background-color: #1565c0;
}

</style>
```



### TravelListDetails.vue

```vue
<template>
  <div id="tavellist-details">
    <p>{{ this.$store.state.selectedCountry }} 여행</p>
    <ul>
      <li v-for="item in filteredItems" :key="item.attraction">
        <span>도시 : {{item.city}}</span><br>
        <span>명소 : {{item.attraction}}</span><br>
        <span>요금 : {{item.entrance_fee | currency}}</span><br>
      </li>
    </ul>
  </div>
</template>

<script>
import {mapGetters} from 'vuex'

export default {
  filters: {
    currency(value) {
      return new Intl.NumberFormat("de-DE", {style: 'currency', currency: 'EUR'}).format(value)
    }
  },
  
  // computed: {
  //   filteredItems() {
  //     return this.$store.state.items.filter(item => {
  //       return item.country == this.$store.state.selectedCountry
  //     })
  //   }
  // }

  computed: {
    // filteredItems() {
    //   return this.$store.getters.filteredItems
    // }
    ...mapGetters(['filteredItems'])
  },



}
</script>

<style scoped>

#tavellist-details {
  color: white;
  background-color: teal;
  padding: 10px 20px;
}
#tavellist-details ul {
  padding: 0;
  list-style-type: none;
}

#tavellist-details li {
  margin: 10px;
  padding: 20px;
  background-color: #00695c;
}

</style>
```









