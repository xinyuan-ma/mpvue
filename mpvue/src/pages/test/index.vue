<template>
	<div class="counter-warp">
		<p>test页面</p>
		<picker @change="bindPickerChange" :value="index" :range="array">
			<view class="picker">
				当前选择：{{array[index]}}
				<!--当前选择：{{item}}-->
			</view>
		</picker>
		<picker @change="bindPicker" :value="index1" :range="array1" range-key="item">
			<view class="picker">
				当前选择：{{array1[index]['item']}}
			</view>
		</picker>
		<radio-group class="radio-group" @change="radioChange">
			<label class="radio" v-for="(item, index) in items" :key="item.name">
				<radio :value="item.name" :checked="item.checked"/>
				{{item.value}}
			</label>
		</radio-group>
		<p>
			<button @click="increment">+</button>
			<button @click="decrement">-</button>
		</p>
		<a href="/pages/yuan/main" class="counter">去往yuan页面</a>
	</div>
</template>

<script>
// Use Vuex
import store from './store'

export default {
  data () {
    return {
      index: 0,
      index1: 0,
      array: ['A', 'B', 'C'],
      array1: [
        {
          item: 'aa', id: 1
        }, {
          item: 'bb', id: 2
        }, {
          item: 'cc', id: 3
        }],
      items: [
        { name: 'USA', value: '美国' },
        { name: 'CHN', value: '中国', checked: 'true' },
        { name: 'BRA', value: '巴西' },
        { name: 'JPN', value: '日本' },
        { name: 'ENG', value: '英国' },
        { name: 'TUR', value: '法国' }
      ]
    }
  },
  computed: {
    count () {
      return store.state.count
    }
  },
  onLoad: function (options) {
    // 生命周期函数--监听页面加载
    console.log('test1 onLoad')
  },
  onReady: function () {
    // 生命周期函数--监听页面初次渲染完成
    console.log('test1 onReady')
  },
  onShow: function () {
    // 生命周期函数--监听页面显示
    console.log('test1 onShow')
  },
  onHide: function () {
    // 生命周期函数--监听页面隐藏
    console.log('test1 onHide')
  },
  onUnload: function () {
    // 生命周期函数--监听页面卸载
    console.log('test1 onUnload')
  },
  onPullDownRefresh: function () {
    // 页面相关事件处理函数--监听用户下拉动作
    console.log('test1 onPullDownRefresh')
  },
  onReachBottom: function () {
    // 页面上拉触底事件的处理函数
    console.log('test1 onReachBottom')
  },
  methods: {
    radioChange (e) {
      console.log('radio发生change事件，携带value值为：', e.target.value)
    },
    bindPickerChange (e) {
      console.log(e.target.value)
      console.log(e)
      this.index = e.target.value * 1
    },
    bindPicker (e) {
      console.log(111111, e.target.value)
      console.log(e)
      this.index1 = e.target.value * 1
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
