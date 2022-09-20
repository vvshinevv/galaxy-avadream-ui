<template>
  <section class="section4">
    <img :src="titleUrl" class="section4-title pc-only" />
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
        :navigation="false"
        :loop="true"
        :pagination="{
          clickable: true,
        }"
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
          <div class="image-card-box" @click="showCard = true">
            <img :src="image.src" class="image-card" />
          </div>
        </swiper-slide>
      </swiper>
    </div>

    <div class="section4-swiper mobile-only">
      <ul class="mobile-card">
        <li
          v-for="(moUrl, index) in imgUrlMo"
          :key="'img' + index"
          @click="showCard = true"
        >
          <img :src="moUrl.src" />
        </li>
      </ul>
    </div>
  </section>
  <!-- 캐릭터 카드 노출 -->
<!--  <ModalCard v-model:visible="showCard" />-->
  <ModalImage :imgUrl="imgComming" :imgUrlMo="imgCommingMo" v-model:visible="showCard"/>
</template>

<script>
import { Autoplay, Navigation } from "swiper";
import { reactive, toRefs } from "vue";
import { Swiper, SwiperSlide } from "swiper/vue";
import ModalCard from "@/components/ModalCard";
// Import Swiper styles
import "swiper/css";
import "swiper/css/navigation";
import WOW from "wowjs";
import ModalImage from "@/components/ModalImage";
export default {
  name: "Section4",
  components: {
    ModalImage,
    Swiper,
    SwiperSlide,
    ModalCard,
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
      showCard: false,
      imgComming: require("@/assets/image/img_comming.png"),
      imgCommingMo: require("@/assets/image/img_comming_mo.png"),
      imgUrl: [
        {
          src: require("@/assets/image/section4/img_c_card_1.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_2.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_3.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_4.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_5.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_6.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_7.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_8.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_9.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_10.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_11.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_12.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_13.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_14.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_15.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_16.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_17.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_18.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_19.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_20.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_21.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_22.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_23.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_24.png"),
        },
      ],
      imgUrlMo: [
        {
          src: require("@/assets/image/section4/img_c_card_mo_1.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_2.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_3.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_4.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_5.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_6.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_7.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_8.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_9.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_10.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_11.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_12.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_13.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_14.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_15.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_16.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_17.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_18.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_19.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_20.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_21.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_22.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_23.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_24.png"),
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
