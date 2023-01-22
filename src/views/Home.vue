<template>
  <div class="go-in">
    <img src="../assets/img/home_top.png" height="300px" width="100%">
    <div class="section" v-loading="loading">
      <div class="section-content">
        <div class="content-summary">
          <div class="summary-left">
            <p class="title">公司简介</p>
            <p class="eTitle">ABOUT US</p>
            <p class="content">
              本公司成立于2020年06月29日，注册地位于上海市奉贤区大叶公路8188号8幢，法定代表人为王杰。
              灯树致力打造科技改变生活 创造改变未来，打造全新的数字化区块链平台，一物一芯，NFC区块链，NFC生态圈，开创全新防伪溯源“芯”篇章，科技防”假”
              经营范围包括许可项目:第二类增值电信业务;住宅室内装饰装修(依法须经批准的项目,经相关部门批准后方可开展经营活动,具体经营项目以审批结果为准)一般项目:技术服务、技术开发、技术咨询、技术交流、技术转让、技术推广;计算机系统服务;信息系统集成服务;数据处理和存储支持服务;软件开发;软件外包服务;财务咨询;社会经济咨询服务;信息咨询服务(不含许可类信息咨询服务);五金产品批发;五金产品零售;建筑材料销售;家具销售;电子产品销售;家用电器销售(除依法须经批准的项目外,凭营业执照依法自主开展经营活动)。
            </p>
          </div>
          <div class="summary-right">
            <img src="../assets/img/home_chatu.jpg" alt mode="aspectFill"/>
          </div>
        </div>
<!--        <el-divider class="el-divider-active">-->
<!--          <i class="el-icon-arrow-down el-icon-arrow-down-active"></i>-->
<!--        </el-divider>-->
        <!-- 发展历程 -->
        <div class="content-course">
          <div class="top">
            <h3>发展历程</h3>
            <p>DEVELOPMENT</p>
            <div class="border"></div>
            <div class="timeline"></div>
          </div>
          <div class="course-time">
            <swiper :options="swiperOption" ref="mySwiper">
              <swiper-slide v-for="(item,index) in courseList" :key="index">
                <div class="time-show">
                  <div class="time-show-item" v-for="(courseOne,one) in item" :key="one">
                    <div class="item-top" :class="{'order-top' : one%2===1}"></div>
                    <el-divider>
                      <i class="el-icon-mobile-phone"></i>
                    </el-divider>
                    <div class="item-bottom" :class="{'order' : one%2===1}">
                      <div class="item-bottom-content">
                        <p>{{ courseOne.Content }}</p>
                        <p>{{ courseOne.Year }}</p>
                      </div>
                    </div>
                  </div>
                </div>
              </swiper-slide>
              <div class="swiper-button-prev" slot="button-prev"></div>
              <div class="swiper-button-next" slot="button-next"></div>
            </swiper>
          </div>
        </div>

        <div class="content-culture">
          <h3>企业文化</h3>
          <h3>CULTURE</h3>
          <p>科技改变生活 创造改变未来</p>
        </div>

      </div>
    </div>
  </div>
</template>

<script>
import Banner from "../components/Banner";

export default {
  components: {
    Banner,
  },
  data() {
    return {
      loading: true,
      honorList: [],
      partnerImg: [],
      courseList: [
        [
          {
            Content: "上海灯树科技有限公司成立",
            Id: 0,
            Year: "2020年6月"
          },
          {
            Content: "确定发展方向",
            Id: 1,
            Year: "2021年7月"
          },
        ],

        [
          {
            Content: "数字化转型，准备搭建区块链（灯树链）生态",
            Id: 2,
            Year: "2022年10月"
          },
          {
            Content: "推出付费问答软件（拜托了App）",
            Id: 2,
            Year: "2023年1月"
          }
        ]
      ],
      teamItem: [],
      swiperOption: {
        navigation: {
          nextEl: ".swiper-button-next",
          prevEl: ".swiper-button-prev"
        }
      },
      dialogTableVisible: false,
      dialogUrl: "",
      dialogTitle: ""
    };
  },
  mounted() {
    this.loading = false;
    // this.$http
    //     .all([
    //       this.$http.get("Honor/GetHonorAll"),
    //       this.$http.get("Enterprise/GetEnterpriseAll"),
    //       this.$http.get(`Team/GetTeamAll`),
    //       this.$http.get(`Course/GetCourseAll`)
    //     ])
    //     .then(
    //         this.$http.spread(
    //             (responseHonor, responseEnterprise, responseTeam, responseCourse) => {
    //               this.honorList = responseHonor.data;
    //               this.partnerImg = responseEnterprise.data;
    //               this.teamItem = responseTeam.data;
    //
    //               var groupCount = Math.ceil(responseCourse.data.length / 2);
    //               window.console.log(groupCount);
    //               for (let i = 0; i < groupCount; i++) {
    //                 let img2 = [];
    //                 for (let j = 0; j < 2; j++) {
    //                   if (responseCourse.data.length - 1 >= i * 2 + j) {
    //                     img2.push(responseCourse.data[i * 2 + j]);
    //                   }
    //                 }
    //                 this.courseList.push(img2);
    //               }
    //               window.console.log(this.courseList);
    //               this.loading = false;
    //             }
    //         )
    //     );
  }
};
</script>

<style lang="scss" scoped>
* {
  margin: 0;
  padding: 0;
}

.go-in {
  width: 100%;
  height: 100%;
  position: relative;
  overflow: hidden;

  .section {
    width: 100%;


    &-content {
      width: 1240px;
      margin: 0 auto;
      background-color: #fff;

      .content-summary {
        //height: 500px;
        display: flex;
        justify-content: space-around;
        padding: 100px 0;

        .summary-left {
          width: 600px;

          .title {
            font-size: 25px;
            color: #e13834;
          }

          .eTitle {
            font-size: 17px;
            color: #e13834;
            padding: 20px 0;
          }

          .content {
            color: #14679f;
            font-size: 14px;
            text-indent: 25px;
            line-height: 30px;
          }
        }

        .summary-right {
          width: 400px;
          height: 310px;
          border: 2px solid #1d42b9;
          //animation: imgboxkey 4s infinite;
          border-radius: 10px;
          margin-top: 80px;
          text-align: center;

          img {
            width: 360px;
            height: 270px;
            margin-top: 20px;
            //animation: imgbo 4s infinite;
          }
        }
      }

      //发展历程
      .content-course {
        padding: 50px 0;
        border-top: 1px solid #3c6088;

        .course-time {
          width: 1000px;
          height: 400px;
          margin: 20px auto;

          .swiper-container {
            height: 100%;
          }

          .time-show {
            width: 700px;
            height: 100%;
            margin: 0 auto;
            display: flex;

            .time-show-item {
              width: 350px;
              height: 100%;
              overflow: hidden;
              display: flex;
              flex-direction: column;

              .item-top,
              .item-bottom {
                height: 190px;
              }

              .item-bottom {
                // display: flex;
                // align-content: center;
                .item-bottom-content {
                  background-color: #1667a0;
                  margin: 20px 0;

                  p {
                    color: #fff;
                    text-align: center;
                    padding: 15px;
                  }
                }
              }
            }
          }
        }
      }

      //企业文化
      .content-culture {
        height: 450px;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: flex-start;
        padding-left: 100px;
        border-bottom: 1px solid #3c6088;
        border-top: 1px solid #3c6088;

        h3 {
          color: #3c6088;
          font-size: 26px;
        }

        p {
          color: #3c6088;
          font-size: 26px;
          padding: 5px 0;
        }

        span {
          font-weight: 400;
          line-height: 36px;
          font-size: 18px;
          padding: 5px 0;
        }
      }

      //公司荣誉
      .content-honor {
        padding: 50px 0;

        .honor-show {
          width: 1000px;
          margin: 30px auto;
          display: flex;
          flex-wrap: wrap;
          justify-content: flex-start;
          align-content: flex-start;

          li {
            width: 220px;
            height: 320px;
            margin-left: 15px;
            list-style: none;
            border: 1px solid palegoldenrod;

            img {
              width: 100%;
              height: 100%;
            }
          }
        }

        p {
          text-align: center;
          color: #3c6088;
        }
      }

      //团队风采
      .content-team {
        padding: 50px 100px;

        .swiper-img {
          height: 400px;
          background: no-repeat center;
          background-size: cover;
        }
      }

      //合作伙伴
      .content-partner {
        padding: 50px 0;

        .partner-img {
          width: 950px;
          margin: 20px auto;
          display: flex;
          justify-content: flex-start;
          flex-wrap: wrap;

          li {
            width: 107px;
            height: 107px;
            list-style: none;
            margin: 10px 25px;

            img {
              width: 100%;
              height: 100%;
              border: 1px solid rgb(194, 218, 235);
            }
          }
        }
      }
    }
  }
}

@keyframes imgboxkey {
  0% {
    border: solid rgb(29, 66, 185) 2px;
  }
  40% {
    border: solid rgb(255, 255, 255) 2px;
  }
  60% {
    border: solid rgb(255, 255, 255) 2px;
  }
  100% {
    border: solid rgb(29, 66, 185) 2px;
  }
}

@keyframes imgbo {
  0% {
    transform: scale(1);
    box-shadow: 0px 0px 0px 0px #ababab;
  }
  50% {
    transform: scale(1.1);
    box-shadow: 0px 0px 10px 5px #ababab;
  }
  100% {
    transform: scale(1);
    box-shadow: 0px 0px 0px 0px #ababab;
  }
}

.el-divider--horizontal {
  margin: 1px 0;
}

.top {
  h3,
  p {
    text-align: center;
    color: #3c6088;
    font-weight: 400;
    padding: 10px 0;
  }

  h3 {
    font-size: 30px;
  }

  p {
    font-size: 20px;
  }

  .border {
    border-bottom: 1px solid #3c6088;
    width: 15%;
    margin: 0 auto;
  }
}

// .swiper-button-disabled {
//   display: none;
// }
.order {
  order: -1;
}

.order-top {
  order: 1;
}

.el-divider {
  background-color: red;
  height: 3px;

  .el-divider__text {
    width: 20px;
    height: 20px;
    border-radius: 50%;
    padding: 0px;
    color: #fff;
    border: 3px solid red;
  }
}

.el-divider-active {
  background-color: #3c6088;
}

.honor-big-img {
  width: 100%;
  height: 100%;
  z-index: 10;
  text-align: center;
  padding-bottom: 20px;
  padding: 5%;
  //background-color: #14679f;
  .el-dialog__wrapper {
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    overflow: auto;
    margin: 0;

    .el-dialog__body {
      overflow: hidden;

      img {
        width: 100%;
      }
    }
  }
}
</style>
