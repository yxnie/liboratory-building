<template>
  <div class="box" :class="{ bg: status === 1 }">
    <img src="../../assets/images/search.svg" alt="">
    <input
      placeholder="搜素 课程/问答"
      class="input"
      @blur="status = 0"
      @focus="status = 1"
    />
  </div>
</template>

<script>
export default {
  name: "InputBox",
  components: {},
  props: {},
  data() {
    return {
      status: 0
    };
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
.box {
  height: 20px;
  width: 143px;
  border: 1px solid #e7eaed;
  border-radius: 5px;
  position: relative;
  padding: 4px 30px 4px 8px;
  top: 16px;
}
.bg {
  border-color: #08bf91;
}
img {
  position: absolute;
  right: 10px;
  top: 7px;
}
input {
  outline: none;
  width: 100%;
  height: 100%;
  border: 0;
}
</style>
