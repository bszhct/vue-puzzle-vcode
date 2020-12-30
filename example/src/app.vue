<template>
  <div>
    <AuthModelMy :show="show"  :pinPosition="pos" :canvasWidth="canvasWidth" :canvasHeight="canvasHeight"
                 @close="onTestClose" @success="onSuccess" :reload="onReload" />

    <hr />
    <button @click="onTest">验证</button>
  </div>
</template>
<script>
import AuthModelMy from "../../dist/main.js";
// import AuthModelMy from "../../src/app.vue";
import Img1 from "./assets/1.jpg";
export default {
  data() {
    return {
      imgs: [Img1],
      show: true,
      // 画布宽高
      canvasWidth: 400,
      canvasHeight: 300,
      // 后端生成的坐标
      pos: [200, 240]
    };
  },
  components: {
    AuthModelMy
  },
  mounted() {
    // AuthModelMy({
    //   show: this.show
    // });
  },
  methods: {
    onTest() {
      this.show = true;
    },
    onTestClose() {
      console.log("出发：", this.show);
      this.show = false;
    },
    onSuccess (a, b) {
      console.log('onSuccess', a, b)
      this.show = false;
    },
    onReload (callback) {
      setTimeout(() => {
        callback()
      }, 1000)
    }
  }
};
</script>