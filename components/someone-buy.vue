<!--
   弹幕谁再买
  listData  数据源列表
  bgColor  item背景颜色
  number   同时出现个数

listData:[
    {
      avatar:'https://wx.qlogo.cn/mmopen/vi_32/DYAIOgq83ephDYYLrWBibN0Y7bERhf1dDsFZgnyickarzzpykG83ibRnHHo7iaQthYwfEvTomNIeRTnlMDC6skFIVA/132',
      uname:'小萍...',
      write:'购买了商品'
    },
    .....
 ]


 -->
<template>
	<view class="someone-buy" :style="[{height:(upx*40*number + upx*10*(number-1)) +'px'}]">
    <view class="item-wrapper item-wrapper-1">
      <view class="item" v-for="(item,index) in listDataA" :key="index" :style="[{background:bgColor}]">
        <view class="user-avatar">
          <image class="img" :src="item.avatar" mode="widthFix"></image>
        </view>
        <view class="user-name">{{item.uname}}</view>
        <view class="description">{{item.write}}</view>
      </view>
    </view><!-- /.item-wrapper -->
		<view class="item-wrapper item-wrapper-2">
		  <view class="item" v-for="(item,index) in listDataB" :key="index" :style="[{background:bgColor}]">
		    <view class="user-avatar">
		      <image class="img" :src="item.avatar" mode="widthFix"></image>
		    </view>
		    <view class="user-name">{{item.uname}}</view>
		    <view class="description">{{item.write}}</view>
		  </view>
		</view><!-- /.item-wrapper -->
	</view>
</template>

<script>
	export default {
    props:{
      listData: {
      	type: Array
      },
      bgColor:{//背景
        type:String,
        default:'rgba(0,0,0,.4)'
      },
      number:{//同时显示多少个
        type:Number,
        default:1,
      }
    },
    name:'someone-buy',
		data() {
			return {
        upx:1,
			};
		},
    computed: {
      listDataA:function(){
        return this.listData.slice(0,9)
      },
      listDataB:function(){
        return this.listData.slice(9,18)
      }
    },
    mounted:function(){
      this.calculateHeight()
    },
    methods:{
      calculateHeight:function(){
        let _this = this
        uni.getSystemInfo({
          success: function (res) {
            _this.upx = res.windowWidth/750
          }
        });
      }
    }
	}
</script>

<style scoped lang="scss">
  .someone-buy{
    position:absolute;
    width: 100%;
    top:0;
    left:0;
    z-index:2;
    overflow: hidden;
  }
  .item-wrapper{
		position: absolute;
		top: 100%;
		left:0;
    display:inline-block;
  }
	.item-wrapper-1 {
	  animation: topSlip 60s linear -30s infinite;
	}

	.item-wrapper-2 {
	  animation: topSlip 60s linear 0s infinite;
	}
  .item{
    display: flex;
    align-items: center;
    justify-content: flex-start;
    font-size:20upx;
    height: 40upx;
    border-radius:40upx;
    padding:0 10upx;
    color: #fff;
    margin-top:10upx;
    .user-avatar{
      width:32upx;
      height:32upx;
      border-radius:32upx;
      overflow: hidden;
      margin-right:10upx;
      .img{
        width:32upx;
        height:32upx;
        border-radius:32upx;
      }
    }
    .user-name{
      max-width: 100upx;
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
    }
  }

	@keyframes topSlip {
	  0% {
	    transform: translate(0,0);
	  }

	  2.77% {
	    transform: translate(0,-11.11%);
	  }

	  5.55% {
	    transform: translate(0,-11.11%);
	  }

	  8.33% {
	    transform: translate(0,-22.22%);
	  }

	  11.1% {
	    transform: translate(0,-22.22%);
	  }

	  13.88% {
	    transform: translate(0,-33.33%);
	  }

	  16.66% {
	    transform: translate(0,-33.33%);
	  }

	  19.43% {
	    transform: translate(0,-44.44%);
	  }

	  22.21% {
	    transform: translate(0,-44.44%);
	  }

	  25% {
	    transform: translate(0,-55.55%);
	  }

	  27.77% {
	    transform: translate(0,-55.55%);
	  }

	  30.54% {
	    transform: translate(0,-66.66%);
	  }

	  33.32% {
	    transform: translate(0,-66.66%);
	  }

	  36% {
	    transform: translate(0,-77.77%);
	  }

	  38.87% {
	    transform: translate(0,-77.77%);
	  }

	  41.6% {
	    transform: translate(0,-88.88%);
	  }

	  44.43% {
	    transform: translate(0,-88.88%);
	  }

	  47.2% {
	    transform: translate(0,-100%);
	  }

	  50% {
	    transform: translate(0,-100%);
	  }

	  52.76% {
	    transform: translate(0,-111.1%);
	  }

	  55.54% {
	    transform: translate(0,-111.1%);
	  }

	  58.31% {
	    transform: translate(0,-122.21%);
	  }

	  61% {
	    transform: translate(0,-122.21%);
	  }

	  63.87% {
	    transform: translate(0,-133.31%);
	  }

	  66.64% {
	    transform: translate(0,-133.31%);
	  }

	  69.42% {
	    transform: translate(0,-144.43%);
	  }

	  72.2% {
	    transform: translate(0,-144.43%);
	  }

	  75% {
	    transform: translate(0,-155.54%);
	  }

	  77.75% {
	    transform: translate(0,-155.54%);
	  }

	  80.5% {
	    transform: translate(0,-166.64%);
	  }

	  83.31% {
	    transform: translate(0,-166.64%);
	  }

	  86% {
	    transform: translate(0,-177.76%);
	  }

	  88.86% {
	    transform: translate(0,-177.76%);
	  }

	  91.64% {
	    transform: translate(0,-188.87%);
	  }

	  94.4% {
	    transform: translate(0,-188.87%);
	  }

	  97.2% {
	    transform: translate(0,-200%);
	  }

	  100% {
	    transform: translate(0,-200%);
	  }
	}
</style>
