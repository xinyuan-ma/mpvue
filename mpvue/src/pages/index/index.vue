<template>
	<div @click="clickHandle" ref="clickHandle">
		<div class="userinfo" @click="bindViewTap">
			<img class="userinfo-avatar" v-if="userInfo.avatarUrl" :src="userInfo.avatarUrl" background-size="cover"/>
			<img class="userinfo-avatar" v-else src="/static/images/user.png" background-size="cover"/>

			<!--<div class="userinfo-nickname">-->
			<!--<card :text="userInfo.nickName"></card>-->
			<!--</div>-->
		</div>

		<div class="usermotto">
			<div class="user-motto">
				<card :text="motto"></card>
			</div>
		</div>
		<div class="count">
			<p class="count_number">{{count}}</p>
			<p>
				<button @click="add">点我+</button>
				<button @click="reduce">点我—</button>
			</p>
		</div>
		<button type="primary" :plain="plain" open-type="getUserInfo" @getuserinfo="bindGetUserInfo" @click="getUserInfoClick">获取权限</button>
		<a href="/pages/counter/main" class="counter">去往Vuex示例页面11</a>
		<a href="/pages/test/main" class="counter">去往test页面</a>
		<a href="/pages/yuan/main" class="counter">去往yuan页面</a>
		<a href="/pages/xin/main" class="counter">去往xin页面</a>

		<div class="all">
			<div class="left">
			</div>
			<div class="right">
			</div>
		</div>
	</div>
</template>

<script>
import card from '@/components/card'

export default {
  data () {
    return {
      count: 0,
      motto: 'Hello mpvue',
      userInfo: {
        nickName: 'mpvue',
        avatarUrl: 'https://wx.qlogo.cn/mmopen/vi_32/Kiam0BsEKCEaFAUAvI1bDXXmBWuOBoA52OoCjzD044fZMrrM6CnfK65uqDiaYiaDdcTWtfHHfKYncibibhjmdnY95ZQ/132'
      },
      plain: true
    }
  },

  components: {
    card
  },

  methods: {
    getUserInfoClick () {
      // console.log('click事件首先触发')
    },
    bindGetUserInfo (e) {
      // console.log('回调事件后触发')
      console.log(e, '用户信息')
    },
    add () {
      this.count += 1
    },
    reduce () {
      this.count -= 1
    },
    bindViewTap () {
      const url = '../logs/main'
      if (mpvuePlatform === 'wx') {
        mpvue.switchTab({ url })
      } else {
        mpvue.navigateTo({ url })
      }
    },
    clickHandle (ev) {
      console.log('clickHandle:', ev)
      // throw {message: 'custom test'}
    }
  },
  created () {
    wx.getSystemInfo({
      success (res) {
        console.log(res)
      }
    })
    const res = wx.getSystemInfoSync()
    console.log(res, 'const res = wx.getSystemInfoSync()')
    console.log(wx.canIUse('getSystemInfoSync'), 'openBluetoothAdapter')
  },
  mounted () {},
  onLoad () {
    console.log('首页onLoad')
  },
  onReady () {
    console.log('首页onReady')
  },
  onShow () {
    console.log('首页onShow')
  }
}
</script>

<style lang="less" scoped>
	.userinfo {
		width: 750rpx;
		/*height: 300rpx;*/
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	.count {
		.count_number {
			text-align: center;
			color: blue;
		}
	}

	.userinfo-avatar {
		width: 300rpx;
		height: 300rpx;
		border-radius: 50%;
	}

	.userinfo-nickname {
		color: #aaa;
	}

	.usermotto {
		/*margin-top: 150px;*/
	}

	.form-control {
		display: block;
		padding: 0 12px;
		margin-bottom: 5px;
		border: 1px solid #ccc;
	}

	.all {
		width: 7.5rem;
		height: 1rem;
		background-color: blue;
	}

	.all:after {
		display: block;
		content: '';
		clear: both;
	}

	.left {
		float: left;
		width: 3rem;
		height: 1rem;
		background-color: red;
	}

	.right {
		float: left;
		width: 4.5rem;
		height: 1rem;
		background-color: green;
	}
</style>
