<template>
  <section class="section4">
<!--    <img :src="titleUrl" class="section4-title" />-->
    <div class="section4-swiper">
      <swiper
        :navigation="true"
        :slides-per-view="2"
        :spaceBetween="0"
        :modules="modules"
        :breakpoints="{
          '768': {
            slidesPerView: 4,
            spaceBetween: 0,
            allowTouchMove: false,
          },
        }"
      >
        <swiper-slide
          v-for="(image, idx) of imgUrl"
          :key="'slide_image_' + idx"
        >
          <div class="image-card-box">
            <img :src="image.src" class="image-card" />
          </div>
        </swiper-slide>
      </swiper>
    </div>
  </section>
</template>

<script>
import { Navigation } from "swiper";
import { reactive, toRefs } from "vue";
import { Swiper, SwiperSlide } from "swiper/vue";

// Import Swiper styles
import "swiper/css";
import "swiper/css/navigation";
import WOW from 'wowjs';
export default {
  name: "Section4",
  components: {
    Swiper,
    SwiperSlide,
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
  setup() {
    const state = reactive({
      titleUrl: require("@/assets/image/section4/img_title.png"),
      imgUrl: [
        {
          src: require("@/assets/image/section4/img_card1.png"),
        },
        {
          src: require("@/assets/image/section4/img_card2.png"),
        },
        {
          src: require("@/assets/image/section4/img_card3.png"),
        },
        {
          src: require("@/assets/image/section4/img_card4.png"),
        },
        {
          src: require("@/assets/image/section4/img_card5.png"),
        },
        {
          src: require("@/assets/image/section4/img_card6.png"),
        },
        {
          src: require("@/assets/image/section4/img_card7.png"),
        },
        {
          src: require("@/assets/image/section4/img_card8.png"),
        },
      ],
    });
    return {
      ...toRefs(state),
      modules: [Navigation],
    };
  },
};
</script>

<style scoped>
.swiper{
    overflow:visible;
}
</style>
