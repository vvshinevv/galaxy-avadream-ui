<template>
  <section class="section5">
    <div class="section5-box">
      <h1>
        <!--        <img :src="titleUrl" class="section5-title-sub" />-->
        <img :src="titleUrl" class="section5-title pc-only" />
      </h1>
      <div class="section5-swiper pc-only">
        <swiper
          :slidesPerView="2"
          :centeredSlides="true"
          :spaceBetween="30"
          :navigation="false"
          :loop="true"
          :autoplay="{
            delay: 2500,
            disableOnInteraction: false,
          }"
          :pagination="{
            clickable: true,
          }"
          :modules="modules"
          @swiper="onSwiper"
        >
          <swiper-slide
            v-for="(image, idx) of imgUrl"
            :key="'slide_image_' + idx"
          >
            <div class="image-card-box" @click="clickPoster(idx)">
              <img :src="image.src" />
            </div>
          </swiper-slide>
        </swiper>
      </div>
      <div class="section5-swiper mobile-only">
        <ul class="section5-mo-list">
          <li
            v-for="(itemMo, idx) of imgUrlMo"
            :key="'slide_' + idx"
            @click="clickPoster(idx)"
          >
            <img :src="itemMo.src" />
          </li>
        </ul>
      </div>
    </div>
  </section>
  <!-- 비디오 노출 -->
  <ModalVideo v-model:visible="showVideo" :movieUrl="movieUrl"/>
</template>
<script>
import { Navigation, Autoplay } from "swiper";
import { reactive, toRefs, watch } from "vue";
import { Swiper, SwiperSlide } from "swiper/vue";
import ModalVideo from "@/components/ModalVideo";

import WOW from "wowjs";
// Import Swiper styles
import "swiper/css";
import "swiper/css/navigation";
export default {
  name: "Section5",
  components: {
    Swiper,
    SwiperSlide,
    ModalVideo,
  },
  mounted() {
    let wow = new WOW.WOW({
      boxClass: "wow",
      animateClass: "animated",
      offset: 0,
      mobile: true,
      live: true,
    });
    wow.init();
  },
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
      titleUrl: require("@/assets/image/section5/img_title_sub_v2.png"),
      posterUrl: require("@/assets/image/section5/img11.png"),
      posterUrlMo: require("@/assets/image/section5/img11_mo.png"),
      showVideo: false,
      imgUrl: [
        {
          type: "img",
          src: require("@/assets/image/section5/img11.png"),
        },
        {
          type: "img",
          src: require("@/assets/image/section5/img22.png"),
        },
        {
          type: "img",
          src: require("@/assets/image/section5/img33_v2.jpg"),
        },
        {
          type: "img",
          src: require("@/assets/image/section5/img44.png"),
        },
      ],
      imgUrlMo: [
        {
          type: "img",
          src: require("@/assets/image/section5/img11_mo.png"),
        },
        {
          type: "img",
          src: require("@/assets/image/section5/img22_mo.png"),
        },
        {
          type: "img",
          src: require("@/assets/image/section5/img33_v2.jpg"),
        },
        {
          type: "img",
          src: require("@/assets/image/section5/img44_mo.png"),
        },
      ],
      isActive: true,
      isActiveMo: true,
        movieUrl:{},
        movieUrlList:[
            {
                url1: require("@/assets/image/section5/img2.webm"),
                url2: require("@/assets/image/section5/img2.mp4"),
            },
            {
               youtubeLink : 'https://www.youtube.com/embed/p4navGrGbj4'
            },
            {
                youtubeLink: 'https://www.youtube.com/embed/58HYg2f8zu8'
            }
        ]
    });
    const videoClick = () => {
      let videoElem = document.getElementById("videoBox2");

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
    const onSwiper = (swiper) => {
      const slides = document.querySelectorAll(".swiper-slide");
      slides.forEach((item) => {
        item.addEventListener("mouseover", (event) => {
          swiper.autoplay.stop();
        });
        item.addEventListener("mouseleave", (event) => {
          swiper.autoplay.start();
        });
      });
    };
    const clickPoster = (index) => {
      if (index === 0) {
        state.showVideo = true;
        state.movieUrl = state.movieUrlList[index];
      }else if(index === 1){
          state.showVideo = true;
          state.movieUrl = state.movieUrlList[index];
      }else if(index === 2){
          state.showVideo = true;
          state.movieUrl = state.movieUrlList[index];
      }
    };
    return {
      ...toRefs(state),
      modules: [Autoplay],
      videoClick,
      onSwiper,
      clickPoster,
    };
  },
};
</script>

<style scoped>
.swiper-slide {
  cursor: pointer;
}
</style>
