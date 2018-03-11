<template>
  <div class="counter-wrap">
    <div class="input-holder">
      <div class="text">
        输入线路编号/站点
      </div>
    </div>
    <!-- 当前行程 -->
    <div class="cur-plan">
      <div class="header">
        当前行程
      </div>
      <div class="cur-coupon">

      </div>
    </div>
    <!-- 推荐线路 -->
    <div class="intro-plan">
      <div class="header">
        推荐线路
      </div>
      <div class="intro-coupon">
        
      </div>
    </div>
    <!-- <p>Vuex counter：{{ count }}</p>
    <p>
      <button @click="increment">+</button>
      <button @click="decrement">-</button>
    </p>

    <a href="/pages/index/index" class="home">去往首页</a> -->
  </div>
</template>

<script>
// Use Vuex
import store from './store'

export default {
  computed: {
    count () {
      return store.state.count
    }
  },
  methods: {
    increment () {
      store.commit('increment')
    },
    decrement () {
      store.commit('decrement')
    }
  }
}

</script>
<style lang="stylus">
.counter-wrap {
  background-color #900
  .input-holder {
    background-color #090
  }
}

</style>
