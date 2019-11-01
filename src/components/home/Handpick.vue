<template>
  <div>
    <div v-for="(item, index) in data" :key="index">
      <!--      标题-->
      <div class="title" v-if="index < 3">
        <span class="big">{{ item.classify_name }}</span
        ><span class="big string">|</span
        ><span class="small">{{ item.description }}</span>
      </div>
      <div class="title" v-else>
        <span class="big">{{ item.classify_name }}</span>
      </div>
      <!--      第一部分图文-->
      <div v-if="index === 0" class="box">
        <div class="top">
          <div class="bigPicture hand">
            <img :src="item.recommend_course.picture_url" alt="" />
          </div>
          <div class="right">
            <div
              v-for="(item1, index1) in item.courses.slice(0, 2)"
              :key="index1"
              class="smallPicture1 hand"
              :class="{ pd: index1 === 0 }"
            >
              <img :src="item1.picture_url" alt="" />
              <div class="word">
                <div class="up">
                  <div class="name">{{ item1.name }}</div>
                  <div class="more">{{ item1.description }}</div>
                </div>
                <div class="student">{{ item1.students_count }}</div>
                <span v-if="item1.fee_type === 'member'" class="member"
                  >会员</span
                >
              </div>
            </div>
          </div>
        </div>
        <div class="foot">
          <div
            v-for="(item1, index1) in item.courses.slice(2)"
            :key="index1"
            class="smallPicture hand"
          >
            <img :src="item1.picture_url" alt="" />
            <div class="word">
              <div class="up">
                <div class="name">{{ item1.name }}</div>
                <div class="more">{{ item1.description }}</div>
              </div>
              <div class="student">
                <img src="../../assets/images/gift.svg" alt="" />
                <span>{{ item1.students_count }}</span>
                <span v-if="item1.fee_type === 'member'" class="member"
                  >会员</span
                >
              </div>
            </div>
          </div>
        </div>
      </div>
      <!--      第二部分-->
      <div v-if="index === 1" class="box box2">
        <swiper :options="swiperOption">
          <swiper-slide
            v-for="(item1, index1) in item.courses"
            :key="index1"
            class="small"
          >
            <div class="soon" v-if="item1.status === 'coming_soon'">
              即将上线
            </div>
            <img :src="item1.picture_url" alt="" />
            <div class="word">
              <div class="up">
                <div class="name">{{ item1.name }}</div>
                <div class="more">{{ item1.description }}</div>
              </div>
              <div class="student">
                <img src="../../assets/images/gift.svg" alt="" />
                <span>{{ item1.students_count }}</span>
                <span
                  v-if="item1.fee_type === 'bootcamp'"
                  class="member member1"
                  >训练营</span
                >
              </div>
            </div>
          </swiper-slide>
          <div class="swiper-button-prev" slot="button-prev"></div>
          <div class="swiper-button-next" slot="button-next"></div>
        </swiper>
      </div>
      <!--      第三部分-->
      <div v-if="index === 2" class="box">
        <div class="foot">
          <div
              v-for="(item1, index1) in item.courses"
              :key="index1"
              class="smallPicture hand"
          >
            <img :src="item1.picture_url" alt="" />
            <div class="word">
              <div class="up">
                <div class="name">{{ item1.name }}</div>
                <div class="more">{{ item1.description }}</div>
              </div>
              <div class="student">
                <img src="../../assets/images/gift.svg" alt="" />
                <span>{{ item1.students_count }}</span>
              </div>
            </div>
          </div>
        </div>
      </div>
      <!--      第四、五部分-->
      <div v-if="index === 3 || index === 4" class="box">
        <div class="foot">
          <div class="font hand"><img :src="item.recommend_course.picture_url" alt=""></div>
          <div class="right">
            <div
                v-for="(item1, index1) in item.courses"
                :key="index1"
                class="smallPicture hand smallPicture2"
            >
              <img :src="item1.picture_url" alt="" />
              <div class="word">
                <div class="up">
                  <div class="name">{{ item1.name }}</div>
                  <div class="more">{{ item1.description }}</div>
                </div>
                <div class="student">
                  <img src="../../assets/images/gift.svg" alt="" />
                  <span>{{ item1.students_count }}</span>
                  <span v-if="item1.fee_type === 'member'" class="member"
                  >会员</span
                  >
                </div>
              </div>
            </div>
          </div>

        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Handpick",
  components: {},
  props: {},
  data() {
    return {
      data: "",
      swiperOption: {
        slidesPerView: 4,
        spaceBetween: 30,
        slidesPerGroup: 4,
        loop: true,
        loopFillGroupWithBlank: true,
        navigation: {
          nextEl: ".swiper-button-next",
          prevEl: ".swiper-button-prev"
        }
      }
    };
  },
  methods: {
    getData() {
      this.$axios
        .req("api/classfication-courses/")
        .then(res => {
          this.data = res;
          console.log(this.data, 1);
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
.swiper-button-prev {
  display: none;
  background: rgba(186, 190, 182, 0.6);
  background-image: url("../../assets/images/wzuojt.svg");
  background-repeat: no-repeat;
  background-position: 15px;
  padding: 10px;
  width: 44px;
  border: 1px solid rgba(186, 190, 182, 0.4);
  border-radius: 50%;
}
.swiper-button-next {
  display: none;
  background: rgba(186, 190, 182, 0.6);
  background-image: url("../../assets/images/wyoujt.svg");
  background-repeat: no-repeat;
  background-position: 15px;
  padding: 10px;
  width: 44px;
  border: 1px solid rgba(186, 190, 182, 0.4);
  border-radius: 50%;
}
.font {
  flex: 0 0 22.5%;
  margin: 0 15px;
  &:hover {
    box-shadow: 3px 3px 5px #cbc9c3;
  }
}
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
.box {
  margin: 0 -15px;
  img {
    display: block;
    width: 100%;
  }
  .top {
    display: flex;
    justify-content: space-between;
    .bigPicture {
      flex: 1;
      margin: 0 15px;
      box-shadow: 0 1px 2px #cbc9c3;
      &:hover {
        box-shadow: 3px 3px 5px #cbc9c3;
      }
    }
    .right {
      flex: 1;
      margin: 0 15px;
      display: flex;
      .smallPicture1 {
        flex: 1;
        box-shadow: 0 1px 2px #cbc9c3;
        &:hover {
          box-shadow: 3px 3px 5px #cbc9c3;
          .word {
            .up {
              top: -63px;
              background: white;
              margin: 0 -10px;
              height: 100px;
              padding-top: 15px;
              .more {
                display: block;
                padding-top: 10px;
              }
            }
          }
        }
      }
      .pd {
        margin-right: 30px;
      }
    }
  }
  .word {
    height: 80px;
    bottom: 0;
    position: relative;
    padding: 20px 10px 0;
    color: #999;
    background: white;
    .up {
      position: relative;
      .more {
        margin: 0 10px;
        display: none;
        font-size: 14px;
        height: 42px;
        overflow: hidden;
      }
      .name {
        margin: 0 10px;
        width: 100%;
        font-size: 16px;
        line-height: 19px;
        height: 19px;
        overflow: hidden;
        text-overflow: ellipsis;
      }
    }
    .student {
      position: absolute;
      bottom: 0;
      font-size: 13px;
      padding: 0 10px;
      height: 53px;
      line-height: 53px;
      width: 100%;
      img {
        display: inline-block;
        width: 12px;
        margin-right: 5px;
      }
      .member {
        position: absolute;
        right: 22%;
        top: 15px;
        background: #ffc500;
        color: white;
        height: 24px;
        line-height: 24px;
        width: 44px;
        text-align: center;
        border-radius: 15px;
      }
      .member1 {
        background: #ff6666;
      }
    }
  }
  .smallPicture {
    flex: 1;
    margin: 0 15px;
    box-shadow: 0 1px 2px #cbc9c3;
    &:hover {
      box-shadow: 3px 3px 5px #cbc9c3;
      .word {
        .up {
          top: -63px;
          background: white;
          margin: 0 -10px;
          height: 100px;
          padding-top: 15px;
          .more {
            display: block;
            padding-top: 10px;
          }
        }
      }
    }
  }
  .foot {
    display: flex;
    justify-content: space-between;
    margin-top: 20px;
    .right {
      flex: 1;
      display: flex;
      flex-wrap: wrap;
      .smallPicture2 {
        flex: 25%;
        overflow: hidden;
      }
    }
  }
}
.box2 {
  margin: 0;
  &:hover {
    .swiper-button-prev {
      display: block;
    }
    .swiper-button-next {
      display: block;
    }
  }
}
.soon {
  position: absolute;
  color: white;
  background: #df6e6a;
  font-size: 13px;
  padding: 5px;
}
.small {
  box-shadow: 0 1px 2px #cbc9c3;
  &:hover {
    box-shadow: 3px 3px 5px #cbc9c3;
    .word {
      .up {
        top: -63px;
        background: white;
        margin: 0 -10px;
        height: 100px;
        padding-top: 15px;
        .more {
          display: block;
          padding-top: 10px;
        }
      }
    }
  }
}
</style>
