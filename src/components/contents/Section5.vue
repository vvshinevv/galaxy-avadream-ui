<template>
  <section class="section5">
    <div class="section5-box">
      <h1>
<!--        <img :src="titleUrl" class="section5-title-sub" />-->
        <img :src="titleUrl2" class="section5-title" />
      </h1>
      <div class="section5-swiper pc-only">
        <swiper
          :slidesPerView="2"
          :centeredSlides="true"
          :spaceBetween="30"
          :allowTouchMove="false"
          :navigation="true"
          :loop="true"
          :autoplay="{
              delay: 2500,
              disableOnInteraction: false,
        }"
          :modules="modules"
        >
          <swiper-slide
            v-for="(image, idx) of imgUrl"
            :key="'slide_image_' + idx"
          >
            <div
              class="image-card-box video section5-video"
              v-if="image.type === 'video'"
            >
              <video
                controls
                style="width: 100%"
                id="videoBox2"
                :poster="posterUrl"
                @playing="updatePaused"
                @pause="updatePaused"
                @canplay="updatePaused"
              >
                <source :src="image.src[0]" type="video/webm" />
                <source :src="image.src[1]" type="video/mp4" />
              </video>
              <div class="icon" v-show="pausedBtn" @click="play"></div>
            </div>
            <div class="image-card-box" v-else>
              <img :src="image.src" />
            </div>
          </swiper-slide>
        </swiper>
      </div>
      <div class="section5-swiper mobile-only">
        <ul class="section5-mo-list">
          <li v-for="(itemMo, idx) of imgUrlMo" :key="'slide_' + idx">
            <video
              controls
              style="width: 100%; object-fit: cover"
              v-if="itemMo.type === 'video'"
              :poster="posterUrlMo"
            >
              <source :src="itemMo.src[0]" type="video/webm" />
              <source :src="itemMo.src[1]" type="video/mp4" />
            </video>
            <img :src="itemMo.src" v-else />
          </li>
        </ul>
      </div>
    </div>
  </section>
</template>

<script>
import { Navigation, Autoplay } from "swiper";
import { reactive, toRefs, watch } from "vue";
import { Swiper, SwiperSlide } from "swiper/vue";

// Import Swiper styles
import "swiper/css";
import "swiper/css/navigation";
export default {
  name: "Section5",
  components: {
    Swiper,
    SwiperSlide,
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
      titleUrl: require("@/assets/image/section5/img_title_sub.png"),
      titleUrl2: require("@/assets/image/section5/img_title.png"),
        posterUrl: require("@/assets/image/section5/img11.png"),
        posterUrlMo: require("@/assets/image/section5/img11_mo.png"),
      imgUrl: [
        {
            type: "video",
            src: [
                require("@/assets/image/section5/img2.webm"),
                require("@/assets/image/section5/img2.mp4"),
            ],
        },
        {
            type: "img",
            src: require("@/assets/image/section5/img22.png"),
        },
      {
          type: "img",
          src: require("@/assets/image/section5/img33.png"),
      },
      {
          type: "img",
          src: require("@/assets/image/section5/img44.png"),
      },
      ],
      imgUrlMo: [
        {
          type: "video",
          src: [
            require("@/assets/image/section5/img2.webm"),
            require("@/assets/image/section5/img2.mp4"),
          ],
        },
          {
              type: "img",
              src: require("@/assets/image/section5/img22_mo.png"),
          },
          {
              type: "img",
              src: require("@/assets/image/section5/img33_mo.png"),
          },
          {
              type: "img",
              src: require("@/assets/image/section5/img44_mo.png"),
          },
      ],
      isActive: true,
      isActiveMo: true,
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
    return {
      ...toRefs(state),
      modules: [Navigation,Autoplay],
      videoClick,
    };
  },
};
</script>

<style scoped></style>
