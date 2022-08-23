<template>
  <section class="section2">
    <img :src="titleUrl" class="section2-title" />
    <div class="section2-video" :class="{ on: isActive }" @click="videoClick">
      <video controls style="object-fit: contain" id="videoBox">
        <source :src="movieUrl" type="video/webm" />
        <source :src="movieUrl2" type="video/mp4" />
      </video>
    </div>
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
      movieUrl: require("@/assets/image/section2/img_movie.webm"),
      movieUrl2: require("@/assets/image/section2/img_movie.mp4"),
      isActive: true,
    });

    const videoClick = () => {
      state.isActive = !state.isActive;
      let videoElem = document.getElementById("videoBox");
      if (state.isActive) {
        return videoElem.play();
      } else {
        return videoElem.pause();
      }
    };
    return {
      ...toRefs(state),
      videoClick,
    };
  },
};
</script>

<style scoped></style>
