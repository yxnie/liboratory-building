<template>
  <div>
    <div class="title">
      <span class="big">楼+ 实战课程</span><span class="big string">|</span
      ><span class="small">定期开班，导师助教全程辅导，最快最优成长</span>
    </div>
    <div class="center">
      <div v-for="(item, index) in data.slice(0, 4)" :key="index" class="obj hand">
        <div class="box">
          <div class="img"><img :src="item.picture_url" alt="" /></div>
          <div class="foot">
            <div class="title1">{{item.title}}</div>
            <div class="time">最近班次 : {{item.open_time}}</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Floor",
  components: {},
  props: {},
  data() {
    return {
      data: ""
    };
  },
  methods: {
    getData() {
      this.$axios
        .req("api/louplus/")
        .then(res => {
          this.data = res;
        })
        .catch(err => {
          console.log(err);
        });
    }
  },
  mounted() {
    this.getData();
  },
  created() {},
  filters: {},
  computed: {},
  watch: {},
  directives: {}
};
</script>

<style scoped lang="scss">
.title {
  margin: 30px 0;
  .big {
    color: #565656;
    font-size: 24px;
  }
  .string {
    margin: 0 8px;
  }
  .small {
    color: #666;
    font-size: 14px;
    vertical-align: 2px;
  }
}
.center {
  display: flex;
  justify-content: space-between;
  margin: 0 -15px;
  .obj {
    padding: 0 15px;
    flex: 1;
    .box {
      width: 100%;
      border: 1px solid #bfbdb7;
      border-radius: 8px;
      box-shadow: 0 1px 2px 0 #ddd;
      &:hover {
        box-shadow: 3px 3px 5px #cbc9c3;
      }
    }
    .foot {
      padding: 18px 10px 15px;
      background: #fff;
      border-radius: 0 0 8px 8px;
      .title1 {
        margin-bottom: 6px;
        font-size: 18px;
        height: 18px;
        overflow: hidden;
        text-overflow: ellipsis;
        /*white-space: nowrap;*/
        color: #565656;
      }
      .time {
        margin: 0;
        /*white-space: nowrap;*/
        overflow: hidden;
        height: 18px;
        text-overflow: ellipsis;
        font-size: 16px;
        color: #a4a4a4;
      }
    }
    .img {
      padding: 0 1px;
      img {
        display: block;
        width: 100%;
        border-radius: 8px 8px 0 0;
      }
    }
  }
}
</style>
