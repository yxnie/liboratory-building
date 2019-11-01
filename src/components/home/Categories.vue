<template>
  <div>
    <div class="all">
      <div v-for="(item, index) in data" :key="index" class="desc">
        <div
          class="list"
          :class="{
            aligning:
              index === data.length - 3 ||
              index === data.length - 2 ||
              index === data.length - 1,
            aligning1: index === data.length - 4 || index === data.length - 5
          }"
        >
          <div class="box">
            <span class="name">{{ item.name }}</span>
          </div>
          <div class="top">
            <span
              v-for="(item1, index1) in item.tags"
              :key="index1"
              class="word"
            >
              <span>
                |<span class="tags hand">{{ item1.name }}</span>
              </span>
            </span>
            |
          </div>
          <div class="box1">
            <span class="name">课程推荐</span>
          </div>
          <div>
            <div
              v-for="(item1, index1) in item.recommend_courses"
              :key="index1"
              class="courses hand"
            >
              {{ item1.name }}
            </div>
          </div>
        </div>
        <div class="title">
          <div class="con hand">{{ item.name }}</div>
          <div>
            <span v-for="(item1, index1) in item.tags" :key="index1">
              <span v-if="index1 < 2" class="tags hand">
                {{ item1.name }}
              </span>
            </span>
          </div>
        </div>
      </div>
      <div class="foot"><div>经管专区</div></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Categories",
  components: {},
  props: {},
  data() {
    return {
      data: []
    };
  },
  methods: {
    getData() {
      this.$axios
        .req("api/categories/")
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
.all {
  width: 260px;
  display: flex;
  flex-direction: column;
  height: 520px;
  background: rgba(0, 0, 0, 0.18);
  .desc {
    flex: 1;
    padding: 0 10px;
    width: 240px;
    line-height: 57px;
    color: white;
    position: relative;
    &:hover {
      background: white;
      color: #86847f;
      .list {
        display: block;
      }
    }
    .list {
      display: none;
      position: absolute;
      left: 258px;
      width: 360px;
      padding: 20px;
      background: white;
      line-height: 20px;
      font-size: 13px;
      .courses {
        margin: 7px 0;
      }
      .box {
        margin-bottom: 10px;
      }
      .box1 {
        margin: 20px 0;
      }
      .name {
        padding: 5px;
        background: #e9ebee;
      }
      .top {
        width: 360px;
        .word {
          padding: 10px 0;
          display: inline-block;
          .tags {
            padding: 7px;
          }
        }
      }
    }
    .aligning {
      bottom: 0;
    }
    .aligning1 {
      top: -40px;
    }
    .title {
      display: flex;
      width: 100%;
      border-bottom: 1px solid #bcbcbc;
      .con {
        margin-right: 10px;
      }
      .tags {
        font-size: 13px;
        margin-right: 7px;
      }
    }
  }
  .foot {
    flex: 1;
    line-height: 50px;
    text-align: center;
    color: white;
  }
}
.hand:hover {
  color: #08bf91;
}
</style>
