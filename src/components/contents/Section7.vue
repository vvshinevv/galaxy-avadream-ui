<template>
  <section class="section7">
    <div class="section7-box">
      <h1>
        <img :src="titleUrl" class="section7-title-sub" />
        <img :src="titleUrl2" class="section7-title" />
      </h1>
      <div class="section7-swiper">
        <swiper
            :navigation="true"
            :slidesPerView="'auto'"
            :spaceBetween="30"
            :modules="modules"
            :breakpoints="{
          '320': {
            spaceBetween: 20,
          },
        }"
        >
          <swiper-slide
              v-for="(image, idx) of imgUrl"
              :key="'slide_image_' + idx"
          >
            <div class="image-card-box" :style="back">
              <img :src="image.src" class="image-card" />
            </div>
          </swiper-slide>
        </swiper>
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
  name: "Section7",
  components: {
    Swiper,
    SwiperSlide,
  },
  setup() {
    const state = reactive({
      titleUrl: require("@/assets/image/section7/img_title_sub.png"),
      titleUrl2: require("@/assets/image/section7/img_title.png"),
      imgUrl: [
        {
          src: require("@/assets/image/section7/img1.png"),
        },
        {
          src: require("@/assets/image/section7/img2.png"),
        },
        {
          src: require("@/assets/image/section7/img2.png"),
        },
        {
          src: require("@/assets/image/section7/img2.png"),
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
