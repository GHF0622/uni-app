<!-- 授权组件 
	交互js 
	
	数据结构
	authStatus是否显示授权组件 true为显示,false不显示
-->
<template>
	<view class="authInfo">
		<button open-type="getUserInfo"  @getuserinfo="getuserinfo" class="authInfoBtn"></button>
	</view>
</template>

<script>
	import {
		mapState,
		mapActions
	} from 'vuex';
	export default {
		name: 'authInfo',
		data() {
			return {
				authStatus: true //判断是否显示授权组建
			};
		},
		mounted() {
			//從VueX裡面獲取出用戶信息（后期改成后端参数判断），如果有的話就不再授權
		},
		computed: {
			...mapState('auth', {
				userinfo: (state) => state.user
			})
		},
		methods: {
			getuserinfo: function(e) {
				if (e.detail.errMsg == "getUserInfo:ok") {
					// this.$store.dispatch("auth/updateUserinfo", e.detail.userInfo) //调用vueX更新用户信息
					this.$emit('getUserInfo',true)
				} else {
					this.$emit('getUserInfo',false)
				}
			},

		}
	}
</script>

<style lang="scss">
	.authInfo,
	.authInfoBtn {
		position: absolute;
		top: 0rpx;
		left: 0rpx;
		width: 100%;
		height: 100%;
		z-index: 9;
		background: transparent;
		border: none;
	}

	// button::after {
	// 	border: none;
	// }
</style>
