<template>
  <div class="img-pre-box" @click="imgClose('close')">
    <el-image class="u-img-pre" alt="图片资料" :src="imgUrl" fit="contain" />
  </div>
</template>

<script>
// import picZoom from "vue-piczoom";
export default {
  props: {
    url: {
      type: String
    }
  },
  mounted() {
    // 绑定键盘事件
    window.addEventListener("keyup", this.imgClose, false);
  },
  methods: {
    imgClose(e) {
      if (e == "close") {
        this.$emit("closeImg");
        return;
      }

      if (e.keyCode === 27) {
        this.$emit("closeImg");
      }
    }
  },
  computed: {
    imgUrl() {
      return this.url;
    }
  },
  beforeDestroy() {
    // 卸载键盘事件
    window.removeEventListener("keyup", this.imgClose, false);
  }
};
</script>

<style lang="scss">
.img-pre-box {
  position: absolute;
  top: 5%;
  left: 10%;
  width: 80%;
  height: 90%;
  z-index: 99;
  background-color: #fff;
  text-align: center;

  >.u-img-pre {
    width: 100%;
    height: 100%;
  }
}
</style>


