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
          src: require("@/assets/image/section4/img_c_card_open11.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_open12.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_open13.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_open14.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_open18.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_open17.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_open16.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_open15.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_open19.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_open20.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_open21.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_open22.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_open23.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_open24.png"),
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
          src: require("@/assets/image/section4/img_c_card_mo_open11.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_open12.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_open13.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_open14.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_open18.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_open17.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_open16.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_open15.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_open19.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_open20.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_open21.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_open22.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_open23.png"),
        },
        {
          src: require("@/assets/image/section4/img_c_card_mo_open24.png"),
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
        {
          char1: require("@/assets/image/pc_card/char13.png"),
          charTitle1: require("@/assets/image/pc_card/charTitle13.png"),
          charTitleSub1: require("@/assets/image/pc_card/charTitleSub13.png"),
          charVideo1: require("@/assets/image/pc_card/charVideo13.png"),
          charText: "싼티안나 이야기 보러가기",
          videoUrl: "https://www.youtube.com/embed/ZP7cD-xSGY8",
        },
        {
          char1: require("@/assets/image/pc_card/char14.png"),
          charTitle1: require("@/assets/image/pc_card/charTitle14.png"),
          charTitleSub1: require("@/assets/image/pc_card/charTitleSub14.png"),
          charVideo1: require("@/assets/image/pc_card/charVideo14.png"),
          charText: "치유신 이야기 보러가기",
          videoUrl: "https://www.youtube.com/embed/6wJFRF591Dw",
        },
        {
          char1: require("@/assets/image/pc_card/char11.png"),
          charTitle1: require("@/assets/image/pc_card/charTitle11.png"),
          charTitleSub1: require("@/assets/image/pc_card/charTitleSub11.png"),
          charVideo1: require("@/assets/image/pc_card/charVideo11.png"),
          charText: "돈벼락 이야기 보러가기",
          videoUrl: "https://www.youtube.com/embed/Xa-7aJnQs_w",
        },
        {
          char1: require("@/assets/image/pc_card/char12.png"),
          charTitle1: require("@/assets/image/pc_card/charTitle12.png"),
          charTitleSub1: require("@/assets/image/pc_card/charTitleSub12.png"),
          charVideo1: require("@/assets/image/pc_card/charVideo12.png"),
          charText: "미스터리 이야기 보러가기",
          videoUrl: "https://www.youtube.com/embed/g0_ANTcQ3WY",
        },
        {
          char1: require("@/assets/image/pc_card/char18.png"),
          charTitle1: require("@/assets/image/pc_card/charTitle18.png"),
          charTitleSub1: require("@/assets/image/pc_card/charTitleSub18.png"),
          charVideo1: require("@/assets/image/pc_card/charVideo18.png"),
          charText: "MC하대수 이야기 보러가기",
          videoUrl: "https://www.youtube.com/embed/1dYjpfVIPmY",
        },
        {
          char1: require("@/assets/image/pc_card/char17.png"),
          charTitle1: require("@/assets/image/pc_card/charTitle17.png"),
          charTitleSub1: require("@/assets/image/pc_card/charTitleSub17.png"),
          charVideo1: require("@/assets/image/pc_card/charVideo17.png"),
          charText: "피어나 공주 이야기 보러가기",
          videoUrl: "https://www.youtube.com/embed/O4Ij4BABUxs",
        },
        {
          char1: require("@/assets/image/pc_card/char16.png"),
          charTitle1: require("@/assets/image/pc_card/charTitle16.png"),
          charTitleSub1: require("@/assets/image/pc_card/charTitleSub16.png"),
          charVideo1: require("@/assets/image/pc_card/charVideo16.png"),
          charText: "특수요원 진 이야기 보러가기",
          videoUrl: "https://www.youtube.com/embed/zpYueIJEAZI",
        },
        {
          char1: require("@/assets/image/pc_card/char15.png"),
          charTitle1: require("@/assets/image/pc_card/charTitle15.png"),
          charTitleSub1: require("@/assets/image/pc_card/charTitleSub15.png"),
          charVideo1: require("@/assets/image/pc_card/charVideo15.png"),
          charText: "동보희 이야기 보러가기",
          videoUrl: "https://www.youtube.com/embed/U2d-hqkKVVM",
        },
        {
          char1: require("@/assets/image/pc_card/char19.png"),
          charTitle1: require("@/assets/image/pc_card/charTitle19.png"),
          charTitleSub1: require("@/assets/image/pc_card/charTitleSub19.png"),
          charVideo1: require("@/assets/image/pc_card/charVideo19.png"),
          charText: "공차니 이야기 보러가기",
          videoUrl: "https://www.youtube.com/embed/BcXrcw4LtpA",
        },
        {
          char1: require("@/assets/image/pc_card/char20.png"),
          charTitle1: require("@/assets/image/pc_card/charTitle20.png"),
          charTitleSub1: require("@/assets/image/pc_card/charTitleSub20.png"),
          charVideo1: require("@/assets/image/pc_card/charVideo20.png"),
          charText: "세일러맨 이야기 보러가기",
          videoUrl: "https://www.youtube.com/embed/Y3LHnl6Gr8Y",
        },
        {
          char1: require("@/assets/image/pc_card/char21.png"),
          charTitle1: require("@/assets/image/pc_card/charTitle21.png"),
          charTitleSub1: require("@/assets/image/pc_card/charTitleSub21.png"),
          charVideo1: require("@/assets/image/pc_card/charVideo21.png"),
          charText: "추앙애 이야기 보러가기",
          videoUrl: "https://www.youtube.com/embed/Nso8u3VYUOw",
        },
        {
          char1: require("@/assets/image/pc_card/char22.png"),
          charTitle1: require("@/assets/image/pc_card/charTitle22.png"),
          charTitleSub1: require("@/assets/image/pc_card/charTitleSub22.png"),
          charVideo1: require("@/assets/image/pc_card/charVideo22.png"),
          charText: "조광남 이야기 보러가기",
          videoUrl: "https://www.youtube.com/embed/VKlFcnkNxiA",
        },
        {
          char1: require("@/assets/image/pc_card/char23.png"),
          charTitle1: require("@/assets/image/pc_card/charTitle23.png"),
          charTitleSub1: require("@/assets/image/pc_card/charTitleSub23.png"),
          charVideo1: require("@/assets/image/pc_card/charVideo23.png"),
          charText: "주미호 이야기 보러가기",
          videoUrl: "https://www.youtube.com/embed/1fyhhKQlcIY",
        },
        {
          char1: require("@/assets/image/pc_card/char24.png"),
          charTitle1: require("@/assets/image/pc_card/charTitle24.png"),
          charTitleSub1: require("@/assets/image/pc_card/charTitleSub24.png"),
          charVideo1: require("@/assets/image/pc_card/charVideo24.png"),
          charText: "김나비 이야기 보러가기",
          videoUrl: "https://www.youtube.com/embed/GSFBtvATNw0",
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
        case 10:
          state.showCard = true;
          state.chacCardData = state.charCard[index];
          break;
        case 11:
          state.showCard = true;
          state.chacCardData = state.charCard[index];
          break;
        case 12:
          state.showCard = true;
          state.chacCardData = state.charCard[index];
          break;
        case 13:
          state.showCard = true;
          state.chacCardData = state.charCard[index];
          break;
        case 14:
          state.showCard = true;
          state.chacCardData = state.charCard[index];
          break;
        case 15:
          state.showCard = true;
          state.chacCardData = state.charCard[index];
          break;
        case 16:
          state.showCard = true;
          state.chacCardData = state.charCard[index];
          break;
        case 17:
          state.showCard = true;
          state.chacCardData = state.charCard[index];
          break;
        case 18:
          state.showCard = true;
          state.chacCardData = state.charCard[index];
          break;
        case 19:
          state.showCard = true;
          state.chacCardData = state.charCard[index];
          break;
        case 20:
          state.showCard = true;
          state.chacCardData = state.charCard[index];
          break;
        case 21:
          state.showCard = true;
          state.chacCardData = state.charCard[index];
          break;
        case 22:
          state.showCard = true;
          state.chacCardData = state.charCard[index];
          break;
        case 23:
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
