<template>
  <div>
    <top class="wrap"></top>
    <div class="banner">
      <categories class="categories"></categories>
      <slideShow></slideShow>
    </div>
    <floor class="wrap"></floor>
    <handpick class="wrap"></handpick>
    <div> </div>
  </div>
</template>

<script>
import top from "../components/home/Top";
import slideShow from "../components/home/SlideShow";
import categories from "../components/home/Categories";
import floor from "../components/home/Floor";
import handpick from "../components/home/Handpick";
export default {
  name: "Home",
  components: {
    top,
    slideShow,
    categories,
    floor,
    handpick
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
.wrap {
  width: 84%;
  margin: 0 auto;
}
.banner {
  position: relative;
}
.categories {
  position: absolute;
  z-index: 99;
  left: 8%;
}
</style>
