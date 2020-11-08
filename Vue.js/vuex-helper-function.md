# Vuex Helper Function

## vuex 헬퍼 함수 사용법

```js
computed: {
  me() {
    return this.$store.state.users.me;
  },
  mainPosts() {
    return this.$store.state.posts.mainPosts;
  },
  hasMorePost() {
    return this.$store.state.posts.hasMorePost;
  }
},
```

```js
removeFollowing(id) {
  this.$store.dispatch('users/removeFollowing', { id });
},
removeFollower(id) {
  this.$store.dispatch('users/removeFollower', { id });
},
```

위를 아래처럼 사용할 수 있다.

```js
computed: {
  ...mapState('users', ['followerList', 'followingList']),
},
methods: {
  ...mapActions('users', ['removeFollower', 'removeFollowing']),
}
```

```js
this['posts/loadPosts']();
```

- [vuex 헬퍼에서 네임스페이스 바인딩](https://vuex.vuejs.org/kr/guide/modules.html#%E1%84%92%E1%85%A6%E1%86%AF%E1%84%91%E1%85%A5%E1%84%8B%E1%85%A6%E1%84%89%E1%85%A5-%E1%84%82%E1%85%A6%E1%84%8B%E1%85%B5%E1%86%B7%E1%84%89%E1%85%B3%E1%84%91%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%89%E1%85%B3-%E1%84%87%E1%85%A1%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%83%E1%85%B5%E1%86%BC)