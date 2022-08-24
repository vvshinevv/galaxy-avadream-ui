<template>
  <section class="section2">
    <img :src="titleUrl" class="section2-title" />
    <div class="section2-video" :class="{ on: isActive }" @click="videoClick">
      <video controls :poster="posterUrl" style="object-fit: contain" id="videoBox"
             @playing="updatePaused"
             @pause="updatePaused"
             @canplay="updatePaused">
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
    data() {
        return {
            videoElement: null,
            pausedBtn: true,
        };
    },
    methods: {
        updatePaused(e) {
            this.videoElement = e.target;
            this.paused = e.target.paused;
            this.pausedBtn = this.paused;
        },
        play() {
            this.videoElement.play();
            this.pausedBtn = false;
        },
        pause() {
            this.videoElement.pause();
            this.pausedBtn = true;
        },
    },
  setup() {
    const state = reactive({
      titleUrl: require("@/assets/image/section2/img_title.png"),
      imgRight: require("@/assets/image/section2/img_right.png"),
      imgLeft: require("@/assets/image/section2/img_left.png"),
      movieUrl: require("@/assets/image/section2/img_movie.webm"),
      movieUrl2: require("@/assets/image/section2/img_movie.mp4"),
      isActive: true,
        posterUrl: require("@/assets/image/section2/img_poster.png"),
    });

      const videoClick = () => {
          let videoElem = document.getElementById("videoBox");

          if (state.isActive) {
              videoElem.play();
              state.isActive = false;
              return;
          } else {
              console.log("멈춤");
              videoElem.pause();
              state.isActive = true;
              return;
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
