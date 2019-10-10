<template>
	<div class="counter-warp">
		<!--<p>xin页面{{count}}</p>-->
		<!--<p>-->
		<!--<button @click="increment">+</button>-->
		<!--<button @click="decrement">-</button>-->
		<!--</p>-->
		<cover-image src="http://hhh.images.visitshanghai.com.cn/nine/education_ad_gn.png"
					 :bindload="bindload"></cover-image>
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
  watch: {
    count (val) {
      console.log('count' + val)
    }
  },
  methods: {
    bindload () {
      console.log('图片加载成功')
    },
    increment () {
      store.commit('increment')
    },
    decrement () {
      store.commit('decrement')
    }
  }
}
</script>

<style>
	.counter-warp {
		text-align: center;
		margin-top: 100px;
	}

	.home {
		display: inline-block;
		margin: 100px auto;
		padding: 5px 10px;
		color: blue;
		border: 1px solid blue;
	}
</style>
