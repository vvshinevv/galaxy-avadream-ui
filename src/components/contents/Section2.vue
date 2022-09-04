<template>
  <section class="section2">
    <img :src="titleUrl" class="section2-title" />
    <div class="section2-video">
      <video controls :poster="posterUrl" style="object-fit: contain" id="videoBox"
             @playing="updatePaused"
             @pause="updatePaused"
             @canplay="updatePaused">
        <source :src="movieUrl" type="video/webm" />
        <source :src="movieUrl2" type="video/mp4" />
      </video>
        <div class="icon" v-show="pausedBtn" @click="play"></div>
    </div>
    <div class="section2-character">
      <img :src="imgPc" class="pc-only" />
      <img :src="imgMo" class="mobile-only" />
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
      imgPc: require("@/assets/image/section2/img_intro.png"),
      imgMo: require("@/assets/image/section2/img_intro_mo.png"),
      movieUrl: require("@/assets/image/section2/img_movie.webm"),
      movieUrl2: require("@/assets/image/section2/img_movie.mp4"),
      isActive: true,
        posterUrl: require("@/assets/image/section2/img_poster_v2.png"),
    });

      const videoClick = () => {
          let videoElem = document.getElementById("videoBox");

          if (state.isActive) {
              videoElem.play();
              state.isActive = false;
              return;
          } else {
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
