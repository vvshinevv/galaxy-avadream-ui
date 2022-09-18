<template>
  <section class="section4">
    <img
      :src="titleUrl"
      class="section4-title pc-only"
    />
    <img
      :src="titleUrl2"
      class="section4-title2 wow fadeInUp pc-only"
      data-wow-duration="1s"
      data-wow-delay="0.5s"
    />
    <div class="section4-swiper pc-only">
      <swiper
        :slidesPerView="4"
        :spaceBetween="0"
        :modules="modules"
        :navigation="false"
        :loop="true"
        :autoplay="{
          delay: 2500,
          disableOnInteraction: false,
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

   <div class="section4-swiper mobile-only">
       <ul class="mobile-card">
           <li v-for="(moUrl,index) in imgUrlMo" :key="'img'+ index">
               <img :src="moUrl.src">
           </li>
       </ul>
   </div>
  </section>
</template>

<script>
import { Autoplay, Navigation } from "swiper";
import { reactive, toRefs } from "vue";
import { Swiper, SwiperSlide } from "swiper/vue";

// Import Swiper styles
import "swiper/css";
import "swiper/css/navigation";
import WOW from "wowjs";
export default {
  name: "Section4",
  components: {
    Swiper,
    SwiperSlide,
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
  setup() {
    const state = reactive({
      titleUrl: require("@/assets/image/section4/img_title2.png"),
      titleUrl2: require("@/assets/image/section4/img_ava.png"),
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
        imgUrlMo: [
            {
                src: require("@/assets/image/section4/img_s1.png"),
            },
            {
                src: require("@/assets/image/section4/img_s2.png"),
            },
            {
                src: require("@/assets/image/section4/img_s3.png"),
            },
            {
                src: require("@/assets/image/section4/img_s4.png"),
            },
            {
                src: require("@/assets/image/section4/img_s5.png"),
            },
            {
                src: require("@/assets/image/section4/img_s6.png"),
            },
            {
                src: require("@/assets/image/section4/img_s1.png"),
            },
            {
                src: require("@/assets/image/section4/img_s2.png"),
            },
            {
                src: require("@/assets/image/section4/img_s3.png"),
            },
            {
                src: require("@/assets/image/section4/img_s4.png"),
            },
            {
                src: require("@/assets/image/section4/img_s5.png"),
            },
            {
                src: require("@/assets/image/section4/img_s6.png"),
            },
            {
                src: require("@/assets/image/section4/img_s1.png"),
            },
            {
                src: require("@/assets/image/section4/img_s2.png"),
            },
            {
                src: require("@/assets/image/section4/img_s3.png"),
            },
            {
                src: require("@/assets/image/section4/img_s4.png"),
            },
            {
                src: require("@/assets/image/section4/img_s5.png"),
            },
            {
                src: require("@/assets/image/section4/img_s6.png"),
            },
            {
                src: require("@/assets/image/section4/img_s1.png"),
            },
            {
                src: require("@/assets/image/section4/img_s2.png"),
            },
            {
                src: require("@/assets/image/section4/img_s3.png"),
            },
            {
                src: require("@/assets/image/section4/img_s4.png"),
            },
            {
                src: require("@/assets/image/section4/img_s5.png"),
            },
            {
                src: require("@/assets/image/section4/img_s6.png"),
            },
        ],
    });
    return {
      ...toRefs(state),
      modules: [Autoplay],
    };
  },
};
</script>

<style scoped></style>
