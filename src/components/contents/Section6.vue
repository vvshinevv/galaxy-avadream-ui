<!-- eslint-disable vue/require-v-for-key -->
<template>
  <section class="section6">
    <div class="pc-only">
      <h1>
        <img :src="titleUrl" class="section6-title-sub" />
        <img :src="titleUrl2" class="section6-title" />
      </h1>
      <div class="section6-swiper">
        <swiper
          :navigation="true"
          :slides-per-view="1"
          :spaceBetween="0"
          :modules="modules"
        >
          <swiper-slide
            v-for="(image, idx) of imgUrl"
            :key="'slide_image_' + idx"
          >
            <ul class="image-card-box">
              <li v-for="item of image.page1">
                <img :src="item" class="image-card" />
              </li>
            </ul>
          </swiper-slide>
        </swiper>
      </div>
    </div>
    <div class="mobile-only">
      <h1>
        <img :src="titleUrlMo" class="section6-title-sub" />
        <img :src="titleUrl2Mo" class="section6-title" />
        <img :src="titleUrl3Mo" class="section6-title-sub2" />
      </h1>
      <div class="section6-swiper">
        <swiper
          :navigation="true"
          :slides-per-view="1"
          :spaceBetween="20"
          :modules="modules"
          :pagination="{
            type: 'progressbar',
          }"
        >
          <swiper-slide
            v-for="(image, idx) of imgUrlMo"
            :key="'slide_image_' + idx"
          >
            <ul class="image-card-box-mo">
              <li v-for="item of image.page1">
                <img :src="item" class="image-card" />
              </li>
            </ul>
          </swiper-slide>
        </swiper>
      </div>
    </div>
  </section>
</template>

<script>
import { Pagination, Navigation } from "swiper";
import { reactive, toRefs } from "vue";
import { Swiper, SwiperSlide } from "swiper/vue";

// Import Swiper styles
import "swiper/css";
import "swiper/css/navigation";
import "swiper/css/pagination";
export default {
  name: "Section6",
  components: {
    Swiper,
    SwiperSlide,
  },
  setup() {
    const state = reactive({
      titleUrl: require("@/assets/image/section6/img_title_sub.png"),
      titleUrl2: require("@/assets/image/section6/img_title.png"),
      titleUrlMo: require("@/assets/image/section6/img_title_sub_mo.png"),
      titleUrl2Mo: require("@/assets/image/section6/img_title_mo.png"),
      titleUrl3Mo: require("@/assets/image/section6/img_title_sub2_mo.png"),
      imgUrl: [
        {
          page1: [
            require("@/assets/image/section6/img_video1.png"),
            require("@/assets/image/section6/img_video2.png"),
            require("@/assets/image/section6/img_video3.png"),
            require("@/assets/image/section6/img_video4.png"),
            require("@/assets/image/section6/img_video5.png"),
            require("@/assets/image/section6/img_video6.png"),
          ],
        },
      ],
      imgUrlMo: [
        {
          page1: [
            require("@/assets/image/section6/img_video1_mo.png"),
            require("@/assets/image/section6/img_video1_mo.png"),
            require("@/assets/image/section6/img_video1_mo.png"),
          ],
        },
        {
          page1: [
            require("@/assets/image/section6/img_video1_mo.png"),
            require("@/assets/image/section6/img_video1_mo.png"),
            require("@/assets/image/section6/img_video1_mo.png"),
          ],
        },
      ],
    });
    return {
      ...toRefs(state),
      modules: [Pagination, Navigation],
    };
  },
};
</script>

<style scoped></style>
