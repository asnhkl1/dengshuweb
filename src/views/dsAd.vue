<template>
  <div class="content">
    <img src="../assets/img/ad_bg.jpeg" class="bg"/>
    <div style="padding-top: 40px;z-index: 99;font-weight: bold;font-size: 45px">新款</div>
    <div style="padding-top: 20px;z-index: 99;;font-weight: bold;font-size: 30px">苹果15 Pro Max 0首付租机</div>
    <img src="../assets/img/phone.png" class="phone"/>
    <div class="goOrder" @click="goAli">点击下单</div>
  </div>
</template>

<script>
export default {
  name: 'dsAd',
  data() {
    return {
      tag: ""
    };
  },
  mounted() {
    const paramsObj = this.getQueryParams(window.location.href)
    if (paramsObj['cp']) {
      this.tag = paramsObj['cp']
    }
  },
  methods: {
    goAli(){
      const url = "https://ds.alipay.com/?scheme=" + encodeURIComponent("alipays://platformapi/startApp?appId=2021004112614346&page=page/tabBar/home/index&query=" + encodeURIComponent("CHANNEL_SCENE=" + this.tag))
      if(this.tag.toUpperCase() == "YPH"){
        window.location.href = "https://blank"
      }else{
        window.location.href = url
      }
    },
    getQueryParams (url) {
      let params = url.split('?')[1];
      // 将参数部分转换为对象
      let paramsObj = {};
      if (params) {
        let paramsArr = params.split('&');
        for (let i = 0; i < paramsArr.length; i++) {
          let param = paramsArr[i].split('=');
          paramsObj[param[0]] = param[1];
        }
      }
      return paramsObj
    }
  }
};
</script>

<style lang="scss" scoped>
.content{
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 100vh;
  position: relative;
}
.bg{
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  width: 100vw;
  height: 100vh;
  z-index: 2;
}
.phone{
  margin-top: 50px;
  height: 100vw;
  z-index: 99;
}
.goOrder{
  position: absolute;
  height: 30px;
  width: 60vw;
  margin: 0 auto;
  bottom: 50px;
  border-radius: 50px;
  z-index: 99;
  color: white;
  border: 2px solid white;
  text-align: center;
  padding-top: 3px;
  font-weight: bold;
  font-size: 20px;
  animation: dmAnimation2 2s linear 1s infinite;
}
@keyframes dmAnimation2 {
  0% {
    transform: scale(1);
    /*开始为原始大小*/
  }

  25% {
    transform: scale(1.2);
    /*放大1.1倍*/
  }

  50% {
    transform: scale(1);
  }

  75% {
    transform: scale(1.2);
  }
}
</style>
