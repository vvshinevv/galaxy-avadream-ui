<template>
  <section class="section2">
    <img :src="titleUrl" class="section2-title wow fadeInUp" data-wow-duration="1s" data-wow-delay="0.5s" />
    <div class="section2-video">
<!--      <video controls :poster="posterUrl" style="object-fit: contain" id="videoBox"-->
<!--             @playing="updatePaused"-->
<!--             @pause="updatePaused"-->
<!--             @canplay="updatePaused">-->
<!--        <source :src="movieUrl" type="video/webm" />-->
<!--        <source :src="movieUrl2" type="video/mp4" />-->
<!--      </video>-->
<!--        <div class="icon" v-show="pausedBtn" @click="play"></div>-->
      <iframe width="100%" style="object-fit: contain;" src="https://www.youtube.com/embed/CcgyExxF2F8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
    </div>
    <div class="section2-character">
      <img :src="imgCard" class="card wow bounceInLeft center" data-wow-duration="1s" data-wow-delay="0.5s"/>
      <img :src="imgCard2" class="card2 wow bounceInRight center" data-wow-duration="1s" data-wow-delay="0.5s"/>
    </div>
  </section>
</template>

<script>
import WOW from 'wowjs';
import { reactive, toRefs } from "vue";

export default {
  name: "Section2",
    data() {
        return {
            videoElement: null,
            pausedBtn: true,
        };
    },
    mounted(){
        let wow = new WOW.WOW({
            boxClass: 'wow',
            animateClass: 'animated',
            offset: 0,
            mobile: true,
            live: true
        });
        wow.init();
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
      titleUrl: require("@/assets/image/section2/img_title_v2.png"),
      imgCard: require("@/assets/image/section2/img_intro_card.png"),
      imgCard2: require("@/assets/image/section2/img_intro_card2.png"),
      movieUrl: require("@/assets/image/section2/img_movie.webm"),
      movieUrl2: require("@/assets/image/section2/img_movie.mp4"),
      isActive: true,
        posterUrl: require("@/assets/image/section2/img_poster_v3.png"),
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

<style scoped>
iframe{
  height: 1000px;

}

@media (min-width: 768px) and (max-width: 1279px){
  iframe{
    height: 600px;

  }
}
@media (max-width: 767px){
  iframe{
    height: 280px;

  }
}
</style>
