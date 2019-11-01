<template>
  <div>
    <swiper :options="swiperOption">
      <swiper-slide v-for="(item, index) in data" :key="index">
        <div class="all" :style="{ background: item.background_color }">
          <img :src="item.picture_url" alt="" />
        </div>
      </swiper-slide>
      <div class="swiper-pagination" slot="pagination"></div>
      <div class="swiper-button-prev" slot="button-prev"></div>
      <div class="swiper-button-next" slot="button-next"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: "SlideShow",
  components: {},
  props: {},
  data() {
    return {
      data: [],
      swiperOption: {
        slidesPerView: 1,
        spaceBetween: 30,
        loop: true,
        centeredSlides: true,
        autoplay: {
          delay: 2500,
          disableOnInteraction: false
        },
        pagination: {
          el: ".swiper-pagination",
          clickable: true
        },
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
        .req("api/banner-pictures/")
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
  width: 84%;
  padding: 0 8%;
}
.swiper-button-prev {
  position: absolute;
  left: 28%;
  height: 40px;
  background-image: url("../../assets/images/left.svg");
}
.swiper-button-next {
  right: 9%;
  background-image: url("../../assets/images/right.svg");
}
img {
  width: 100%;
}
</style>
