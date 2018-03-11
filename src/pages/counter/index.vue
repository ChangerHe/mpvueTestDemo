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
    <div class="map-test">
      <!-- <map id="theMap" style="width: 100%; height:100%" longitude='114.05956' latitude='22.54286' scale='12'/> -->

      <map id="theMap" style="width: 100%; height:100%" :longitude='longitude' :latitude='latitude' scale='12' :markers='markers' @markertap='onMarkerTap' :polyline="polyline" />
      <canvas></canvas>
    </div>
    
    <!-- <p>Vuex counter：{{ count }}</p>
    <p>
      <button @click="increment">+</button>
      <button @click="decrement">-</button>
    </p>test

    <a href="/pages/index/index" class="home">去往首页</a> -->
  </div>
</template>

<script>
// Use Vuex
import store from './store'

export default {
  data () {
    return {
      longitude: '',
      latitude: '',
      polyline: '',
      markers: []
    }
  },
  computed: {
    count () {
      return store.state.count
    }
  },
  created () {
    console.log(wx)
    const _this = this
    wx.getLocation({
      type: 'gcj02',
      success (res) {
        console.log(res)
        _this.longitude = res.longitude
        _this.latitude = res.latitude
        // wx.openLocation({
        //   longitude: res.longitude,
        //   latitude: res.latitude,
        //   scale: 18
        // })
        _this.markers.push({
          id: 1,
          latitude: res.latitude,
          longitude: res.longitude,
          title: 'testMarker',
          iconPath: '/static/icon_pin_red2x.png',
          callout: {
            content: 'testtest',
            color: '#900',
            fontSize: 30,
            bgColor: '#090',
            padding: 30,
            display: 'ALWAYS',
            textAlign: 'center'
          },
          label: {
            content: 'test11111'
          },
          polyline: {
            points: [
              {
                longitude: res.longitude,
                latitude: res.latitude
              },
              {
                longitude: res.longitude - 0.000001,
                latitude: res.latitude - 0.000001
              }
            ],
            color: '#000',
            arrowLine: true,
            borderWidth: 20
          }
        })
      },
      fail (res) {
        console.log(res)
      }
    })
  },
  methods: {
    increment () {
      store.commit('increment')
    },
    decrement () {
      store.commit('decrement')
    },
    onMarkerTap () {
      console.log(1)
    }
  }
}

</script>
<style lang="stylus">
page {
  width: 100%;
  height: 100%;
}
.counter-wrap {
  width 100%
  height: 100%
  background-color #900
  .input-holder {
    background-color #090
  }
  .map-test {
    width: 100%
    height: 100%
  }
}

</style>
