<template>
  <div id="app">
    <el-container>
      <el-header v-show="isShow">
        <div class="logo">
          <img src="./assets/img/dengshu_logo.png" alt />
        </div>
        <el-menu
          :default-active="defaultActive"
          class="el-menu-demo"
          mode="horizontal"
          @select="handleSelect"
          :router="router"
        >
<!--          <el-menu-item index="/">首页</el-menu-item>-->
<!--          <el-menu-item index="/news">新闻资讯</el-menu-item>-->
<!--          <el-menu-item index="/product">产品中心</el-menu-item>-->
<!--          <el-menu-item index="/case">经典案例</el-menu-item>-->
          <el-menu-item index="/goin">首页</el-menu-item>
          <el-menu-item index="/download">旗下产品</el-menu-item>
        </el-menu>
      </el-header>
      <el-main>
        <router-view />
      </el-main>
      <div class="footer" v-show="isShow">
        <div class="footer-content">
          <ul class="content-nav">
            <li>
              <p>走进灯树</p>
              <span>公司简介</span>
            </li>
            <li>
              <p>旗下产品</p>
              <span>拜托了App</span>
            </li>
            <li>
              <p>法律信息</p>
              <span @click="privacy" style="cursor: pointer;">隐私政策</span>
            </li>
            <li>
              <p>联系我们</p>
              <span>邮箱：dencent@lanterntreechain.com</span>
              <span>电话：15303750097</span>
              <span>地址：上海市奉贤区大叶公路8188号8幢</span>
            </li>
          </ul>
        </div>
        <div class="copyright">
          <span>Copyright © 2023 上海灯树科技有限公司版权所有 | 沪ICP备2023000787号</span>
        </div>
      </div>
    </el-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      router: true,
      defaultActive: "/",
      isShow: false
    };
  },
  updated() {
    this.isShow = this.$route.path !== "/privacy" ||this.$route.path !== "/payAgreement"
    window.console.log(this.isShow)
  },
  methods: {
    handleSelect() {
      // window.console.log(this.isShow);
    },
    privacy(){
      window.open("http://www.lanterntreechain.com/#/privacy")
    }
  }
};
</script>

<style lang="scss">
* {
  padding: 0;
  margin: 0;
}
html,
body {
  height: 100%;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

.el-header {
  display: flex;
  justify-content: space-between;
  align-content: center;
  width: 1240px;
  margin: 0 auto;
  //background-color: #fff;

  .logo {
    width: 280px;
    img {
      width: 100%;
      line-height: 60px;
    }
  }
}
.el-main {
  padding: 0 !important;
}

.footer {
  width: 100%;
  overflow: hidden;
  &-content {
    width: 1240px;
    margin: 0 auto;
    padding-top: 20px;
    display: flex;
    justify-content: space-between;
    .content-nav {
      display: flex;
      justify-content: space-around;
      li {
        display: flex;
        flex-direction: column;
        padding: 0 20px;
        //justify-content: center;
        align-items: flex-start;
        p {
          font-size: 20px;
          color: #000000;
          padding: 10px 0;
        }
        span {
          color: #000000;
          font-weight: 300;
          padding: 5px 0;
        }
      }
    }
    img {
      width: 170px;
      height: 170px;
      padding: 10px;
    }
  }
  .copyright {
    height: 30px;
    display: flex;
    justify-content: center;
    span {
      color: #000000;
      line-height: 30px;
    }
  }
}
</style>
