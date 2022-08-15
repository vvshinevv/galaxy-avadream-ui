<template>
  <section class="section5">
    <div class="section5-box">
      <h1>
        <img :src="titleUrl" class="section5-title-sub" />
        <img :src="titleUrl2" class="section5-title" />
      </h1>
      <div class="section5-swiper pc-only">
        <swiper
            :navigation="true"
            :slidesPerView="'auto'"
            :spaceBetween="30"
            :modules="modules"
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
      <div class="section5-swiper mobile-only">
        <ul class="section5-mo-list">
          <li v-for="itemMo of imgUrlMo">
            <img :src="itemMo.src" />
          </li>
        </ul>
      </div>
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
export default {
  name: "Section5",
  components: {
    Swiper,
    SwiperSlide,
  },
  setup() {
    const state = reactive({
      titleUrl: require("@/assets/image/section5/img_title_sub.png"),
      titleUrl2: require("@/assets/image/section5/img_title.png"),
      imgUrl: [
        {
          src: require("@/assets/image/section5/img1.png"),
        },
        {
          src: require("@/assets/image/section5/img2.png"),
        },
        {
          src: require("@/assets/image/section5/img2.png"),
        },
      ],
      imgUrlMo: [
        {
          src: require("@/assets/image/section5/img1_mo.png"),
        },
        {
          src: require("@/assets/image/section5/img2_mo.png"),
        },
        {
          src: require("@/assets/image/section5/img3_mo.png"),
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

<style scoped></style>
