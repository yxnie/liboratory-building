<template>
  <div>
    <div class="top">
      <div class="before">
        <img src="../../assets/images/log.svg" alt="" class="hand" /><span
          class="word"
          >做实验，学编程</span
        >
      </div>
      <div class="back">
        <div class="edition">
          <span class="hand">企业版</span><span class="line">|</span
          ><span class="hand">学校版</span>
        </div>
        <div class="login hand">登录</div>
        <div><button class="hand">注册</button></div>
      </div>
    </div>
    <div class="foot">
      <div class="before">
        <div class="hand div">
          <span><i class="el-icon-s-grid"></i> 全部课程</span>
        </div>
        <div class="word">
          <span class="hand">路径</span>
          <span class="hand">训练营</span>
          <span class="hand">楼+</span>
          <span class="hand"
            >会员<img src="../../assets/images/hot.svg" alt="" class="img"
          /></span>
          <span class="Hand"
            ><div class="title hand">
              社区<i class="el-icon-caret-bottom"></i>
            </div>
            <div class="more">
              <div class="hand">讨论</div>
              <div class="hand">教程库</div>
              <div class="hand">直播</div>
              <div class="hand">比赛</div>
            </div>
          </span>
        </div>
      </div>
      <div class="back"><inputBox></inputBox></div>
    </div>
  </div>
</template>

<script>
import inputBox from "./InputBox";
export default {
  name: "Top",
  components: {
    inputBox
  },
  props: {},
  data() {
    return {};
  },
  methods: {},
  mounted() {},
  created() {},
  filters: {},
  computed: {},
  watch: {},
  directives: {}
};
</script>

<style scoped lang="scss">
.top {
  margin-top: 20px;
  margin-bottom: 20px;
  display: flex;
  justify-content: space-between;
  height: 50px;
  line-height: 50px;
  img {
    display: block;
    height: 50px;
  }
  .before {
    display: flex;
    .word {
      width: 130px;
      font-size: 18px;
      color: #274a59;
    }
  }
  .back {
    display: flex;
    .edition {
      color: #999;
      .hand {
        &:hover {
          color: #08bf91;
        }
      }
      .line {
        margin: auto 8px;
      }
    }
    .login {
      width: 82px;
      text-align: center;
      color: #08bf91;
      &:hover {
        color: #205e1e;
      }
    }
    button {
      height: 50px;
      width: 82px;
      background: #08bf91;
      border: 0;
      color: white;
      font-size: 17px;
    }
  }
}
.foot {
  height: 64px;
  display: flex;
  justify-content: space-between;
  .before {
    line-height: 64px;
    display: flex;
    .word {
      display: flex;
    }
    .Hand {
      &:hover .more {
        display: block;
      }
    }
    .div {
      width: 260px;
      background: #08bf91;
      span {
        padding: 18px;
        font-size: 17px;
        color: white;
      }
    }
    span {
      padding: 0 18px;
      font-size: 16px;
      position: relative;
      .img {
        position: absolute;
        left: 54px;
        top: 8px;
      }
      .more {
        z-index: 99;
        display: none;
        position: absolute;
        width: 100px;
        left: 0;
        padding-left: 18px;
        border-radius: 0 0 5px 5px;
        background: white;
        div {
          height: 40px;
          line-height: 40px;
        }
      }
    }
    .hand:hover {
      color: #08bf91;
    }
  }
  .back {
    margin-right: 15px;
  }
}
</style>
