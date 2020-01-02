<template>
  <view class="marquee">
    <view class="right-slip ">
      <view class="list flex align-center justify-start type-0"  :style="[{width:width+'px','font-size':size*upx+'px',color:color}]"><!-- animation: 'rightSlip '+ second+'s linear '+ -1/2*second+'s infinite', -->
          {{text}}
      </view>
      <view class="list flex align-center justify-start type-1"  :style="[{width:width+'px','font-size':size*upx+'px',color:color}]"><!-- animation: 'rightSlip '+ second+'s linear 0s infinite', -->
          {{text}}
      </view>
    </view>
  </view>
</template>

<script>
  export default {
    props: {
      text: {
        type: String
      },
      size:{
        type:Number
      },
      interval:{
        type:Number
      },
      color:{
        type: String
      }
    },
    computed: {
      width:function(){
        return this.text.length*this.size*this.upx+this.interval*this.upx
      },
      second:function(){
        // parseInt(this.text.length/750/this.size)*20
       return 20;
      }
    },
    name: 'marquee',
    data() {
      return {
        upx:'',//upx
      };
    },
    mounted: function() {
      let _this =this
      uni.getSystemInfo({
        success: function (res) {
          _this.upx = res.windowWidth/750
        },
      })
    },
    methods: {

    }
  }
</script>

<style scoped lang="scss">
  .marquee {
    width: 100%;
    overflow: hidden;
    height: 76upx;
    overflow: hidden;
    position: relative;
    transform: translate3d(0, 0, 0);
  }

  .right-slip {
    overflow: hidden;
    height: 76upx;
    position: relative;
    z-index: 2;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .list {
    display:inline;
    display:inline-block;
    white-space: nowrap;
    position: absolute;
    top: 0;
    left: 100%;
    width: 100%;
    height: 100%;
  }
  @keyframes rightSlip {
    0% {
      transform: translate(0, 0);
    }

    100% {
      transform: translate(-200%, 0);
    }
  }

  .type-0 {
    animation: rightSlip 20s linear -10s infinite;
  }

  .type-1 {
    animation: rightSlip 20s linear 0s infinite;
  }
</style>
