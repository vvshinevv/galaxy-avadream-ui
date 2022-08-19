<template>
  <section class="section2">
    <img :src="titleUrl" class="section2-title" />
    <video controls  style="object-fit: contain;">
      <source :src="movieUrl"
              type="video/mp4">
    </video>
    <div class="section2-character">
      <img :src="imgLeft" class="section2-left" />
      <img :src="imgRight" class="section2-right" />
    </div>
  </section>
</template>

<script>
import { reactive, toRefs } from "vue";

export default {
  name: "Section2",
  setup() {
    const state = reactive({
      titleUrl: require("@/assets/image/section2/img_title.png"),
      imgRight: require("@/assets/image/section2/img_right.png"),
      imgLeft: require("@/assets/image/section2/img_left.png"),
      movieUrl: require("@/assets/image/section2/img_movie.mp4"),
    });
    return {
      ...toRefs(state),
    };
  },
};
</script>

<style scoped></style>
