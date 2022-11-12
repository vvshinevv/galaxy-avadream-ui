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
          <div class="image-card-box" @click="showCardClick(idx)">
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
          @click="showCardClick(index)"
        >
          <img :src="moUrl.src" />
        </li>
      </ul>
    </div>
  </section>
  <!-- 캐릭터 카드 노출 -->
  <ModalCard v-model:visible="showCard" :chacCardData="chacCardData" />
  <ModalImage
    :imgUrl="imgComming"
    :imgUrlMo="imgCommingMo"
    v-model:visible="showCommingSoon"
  />
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
      showCommingSoon: false,
      imgComming: require("@/assets/image/img_comming.png"),
      imgCommingMo: require("@/assets/image/img_comming_mo.png"),
      imgUrl: [
        {
          src: require("@/assets/image/section4/img_c_card_open.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_open2.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_open3.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_open4.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_open5.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_open6.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_8_open.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_7_open.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_9_open.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_10_open.png"),
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
          src: require("@/assets/image/section4/img_c_card_mo_open.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_open2.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_open3.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_open4.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_open5.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_open6.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_open8.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_open7.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_9_open.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_10_open.png"),
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
      chacCardData: {},
      charCard: [
        {
          char1: require("@/assets/image/pc_card/char1.png"),
          charTitle1: require("@/assets/image/pc_card/charTitle1.png"),
          charTitleSub1: require("@/assets/image/pc_card/charTitleSub1.png"),
          charVideo1: require("@/assets/image/pc_card/charVideo1.png"),
          charText: "기록희 이야기 보러가기",
          videoUrl: "https://www.youtube.com/embed/ksQLEGck8JE",
        },
        {
          char1: require("@/assets/image/pc_card/char2.png"),
          charTitle1: require("@/assets/image/pc_card/charTitle2.png"),
          charTitleSub1: require("@/assets/image/pc_card/charTitleSub2.png"),
          charVideo1: require("@/assets/image/pc_card/charVideo2.png"),
          charText: "음원깡패 이야기 보러가기",
          videoUrl: "https://www.youtube.com/embed/ktSDWUQyAsA",
        },
        {
          char1: require("@/assets/image/pc_card/char3.png"),
          charTitle1: require("@/assets/image/pc_card/charTitle3.png"),
          charTitleSub1: require("@/assets/image/pc_card/charTitleSub3.png"),
          charVideo1: require("@/assets/image/pc_card/charVideo3.png"),
          charText: "삐뚜르 빼뚜르 이야기 보러가기",
          videoUrl: "https://www.youtube.com/embed/pos7ZQOH9DM",
        },
        {
          char1: require("@/assets/image/pc_card/char4.png"),
          charTitle1: require("@/assets/image/pc_card/charTitle4.png"),
          charTitleSub1: require("@/assets/image/pc_card/charTitleSub4.png"),
          charVideo1: require("@/assets/image/pc_card/charVideo4.png"),
          charText: "자이언트 손 커엽이 이야기 보러가기",
          videoUrl: "https://www.youtube.com/embed/pK-CM9DV7pw",
        },
        {
          char1: require("@/assets/image/pc_card/char5.png"),
          charTitle1: require("@/assets/image/pc_card/charTitle5.png"),
          charTitleSub1: require("@/assets/image/pc_card/charTitleSub5.png"),
          charVideo1: require("@/assets/image/pc_card/charVideo5.png"),
          charText: "마리앙 이야기 보러가기",
          videoUrl: "https://www.youtube.com/embed/sbdft0Ps9M8",
        },
        {
          char1: require("@/assets/image/pc_card/char6.png"),
          charTitle1: require("@/assets/image/pc_card/charTitle6.png"),
          charTitleSub1: require("@/assets/image/pc_card/charTitleSub6.png"),
          charVideo1: require("@/assets/image/pc_card/charVideo6.png"),
          charText: "반이바니 이야기 보러가기",
          videoUrl: "https://www.youtube.com/embed/93e7iknXdAY",
        },
        {
          char1: require("@/assets/image/pc_card/char8.png"),
          charTitle1: require("@/assets/image/pc_card/charTitle8.png"),
          charTitleSub1: require("@/assets/image/pc_card/charTitleSub8.png"),
          charVideo1: require("@/assets/image/pc_card/charVideo8.png"),
          charText: "플라이 이야기 보러가기",
          videoUrl: "https://www.youtube.com/embed/iAjIQGjars8",
        },
        {
          char1: require("@/assets/image/pc_card/char7.png"),
          charTitle1: require("@/assets/image/pc_card/charTitle7.png"),
          charTitleSub1: require("@/assets/image/pc_card/charTitleSub7.png"),
          charVideo1: require("@/assets/image/pc_card/charVideo7.png"),
          charText: "실리아 이야기 보러가기",
          videoUrl: "https://www.youtube.com/embed/7NNAP--HEFg",
        },
        {
          char1: require("@/assets/image/pc_card/char9.png"),
          charTitle1: require("@/assets/image/pc_card/charTitle9.png"),
          charTitleSub1: require("@/assets/image/pc_card/charTitleSub9.png"),
          charVideo1: require("@/assets/image/pc_card/charVideo9.png"),
          charText: "마!도로스 아이가 이야기 보러가기",
          videoUrl: "https://www.youtube.com/embed/mu10E3bg7og",
        },
        {
          char1: require("@/assets/image/pc_card/char10.png"),
          charTitle1: require("@/assets/image/pc_card/charTitle10.png"),
          charTitleSub1: require("@/assets/image/pc_card/charTitleSub10.png"),
          charVideo1: require("@/assets/image/pc_card/charVideo10.png"),
          charText: "안질리나 젤리곰 이야기 보러가기",
          videoUrl: "https://www.youtube.com/embed/DnDpBULA5-I",
        },
      ],
    });
    const showCardClick = (index) => {
      switch (index) {
        case 0:
          state.showCard = true;
          state.chacCardData = state.charCard[index];
          break;
        case 1:
          state.showCard = true;
          state.chacCardData = state.charCard[index];
          break;
        case 2:
          state.showCard = true;
          state.chacCardData = state.charCard[index];
          break;
        case 3:
          state.showCard = true;
          state.chacCardData = state.charCard[index];
          break;
        case 4:
          state.showCard = true;
          state.chacCardData = state.charCard[index];
          break;
        case 5:
          state.showCard = true;
          state.chacCardData = state.charCard[index];
          break;
        case 6:
          state.showCard = true;
          state.chacCardData = state.charCard[index];
          break;
        case 7:
          state.showCard = true;
          state.chacCardData = state.charCard[index];
          break;
        case 8:
          state.showCard = true;
          state.chacCardData = state.charCard[index];
          break;
        case 9:
          state.showCard = true;
          state.chacCardData = state.charCard[index];
          break;
        default:
          state.showCommingSoon = true;
          break;
      }
    };
    return {
      ...toRefs(state),
      showCardClick,
      modules: [Autoplay],
    };
  },
};
</script>

<style scoped></style>
