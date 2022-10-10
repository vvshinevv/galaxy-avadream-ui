<template>
  <Modal
    :visible="visible"
    @update:visible="$emit('update:visible', false)"
    innerClass="modal-image"
    :showClose="true"
    :dimClose="true"
  >
    <div class="card-char-box pc-only">
      <div class="card-char-img">
        <img :src="chacCardData.char1" />
      </div>
      <div class="card-char-video">
        <img :src="chacCardData.charTitleSub1" class="title" />
        <img :src="chacCardData.charTitle1" class="title" />
        <div class="ytube">
          <img
            :src="chacCardData.charVideo1"
            class="video"
            @click="imgThumbClick"
          />
          <iframe
            id="videoYtube"
            width="100%"
            style="object-fit: contain"
            :src="chacCardData.videoUrl"
            title="YouTube video player"
            frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
            allowfullscreen
          ></iframe>
        </div>
        <div class="char_sns">
          <p class="text">
            {{ chacCardData.charText
            }}<svg
              style="margin-top: -4px; vertical-align: middle"
              xmlns="http://www.w3.org/2000/svg"
              width="48"
              height="48"
              viewBox="0 0 48 48"
            >
              <path
                data-name="사각형 10"
                transform="rotate(180 24 24)"
                style="fill: none"
                d="M0 0h48v48H0z"
              />
              <path
                data-name="패스 1563"
                d="M15.668 0 31.2 23.774H0z"
                transform="rotate(90 14.533 22.933)"
                style="fill: #fff"
              />
            </svg>
          </p>
          <img :src="sns1" class="sns" />
          <img :src="sns2" class="sns2" />
        </div>
      </div>
    </div>
    <div class="card-char-box mobile-only">
      <div class="card-char-img">
        <img :src="chacCardData.charTitleSub1" class="sub-title" />
        <img :src="chacCardData.char1" />
        <img :src="chacCardData.charTitle1" class="title" />
      </div>
      <div class="card-char-video">
        <div class="ytube">
          <img
            :src="chacCardData.charVideo1"
            class="video"
            @click="imgThumbClick"
          />
          <iframe
            id="videoYtube"
            width="100%"
            style="object-fit: contain"
            :src="chacCardData.videoUrl"
            title="YouTube video player"
            frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
            allowfullscreen
          ></iframe>
        </div>
        <div class="char_sns">
          <p class="text">
            {{ chacCardData.charText
            }}<svg
              style="
                margin-top: -2px;
                margin-left: -4px;
                vertical-align: middle;
                transform: scale(0.6);
              "
              xmlns="http://www.w3.org/2000/svg"
              width="48"
              height="48"
              viewBox="0 0 48 48"
            >
              <path
                data-name="사각형 10"
                transform="rotate(180 24 24)"
                style="fill: none"
                d="M0 0h48v48H0z"
              />
              <path
                data-name="패스 1563"
                d="M15.668 0 31.2 23.774H0z"
                transform="rotate(90 14.533 22.933)"
                style="fill: #fff"
              />
            </svg>
          </p>
          <img :src="sns1" class="sns" />
          <img :src="sns2" class="sns2" />
        </div>
      </div>
    </div>
  </Modal>
</template>

<script>
import Modal from "@/components/Modal";
import { reactive, toRefs, onMounted } from "vue";
export default {
  name: "ModalCard",
  components: { Modal },
  props: {
    visible: {
      type: Boolean,
      default: false,
    },
    imgUrl: {
      type: String,
      default: "",
    },
    imgUrlTitle: {
      type: String,
      default: "",
    },
    chacCardData: {
      type: Object,
      default: () => {
        return {};
      },
    },
  },
  setup(props) {
    const state = reactive({
      sns1: require("@/assets/image/pc_card/ico_u.png"),
      sns2: require("@/assets/image/pc_card/ico_in.png"),
    });
    const imgThumbClick = (e) => {
      e.preventDefault();
      const playVideo = event.target;
      playVideo.style.zIndex = -1;
      document.querySelector("#videoYtube").src += "?autoplay=1";
    };
    return {
      imgThumbClick,
      ...toRefs(state),
    };
  },
};
</script>

<style scoped lang="scss">
:deep(.modal-image) {
  max-width: 1920px;
  max-height: 1080px;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  background-image: url("@/assets/image/pc_card/bg.png"),
    linear-gradient(
      62deg,
      #ff005f -9%,
      #ff0468 2%,
      #ff1181 20%,
      #ff26aa 43%,
      #ff28ad 44%,
      #00c0ff 101%
    );
  background-repeat: no-repeat, no-repeat;
  background-position: -400px center, 0 0;
  background-size: cover, contain;
  @media (max-width: 767px) {
    background-position: center, 0 0;
  }
}
.card-char-box {
  display: flex;
  height: 100%;
  img {
    width: 95%;
    @media (max-width: 767px) {
      width: 100%;
    }
  }
}
.card-char-img {
  width: 45%;
  display: flex;
  align-items: flex-end;
  .title {
    margin-top: -40px;
  }
  .sub-title {
  }
  @media (max-width: 767px) {
    flex-direction: column;
    margin: 45px auto 20px;
    width: 60%;
  }
}
.card-char-video {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding-right: 80px;
  @media (min-width: 768px) and (max-width: 1279px) {
    padding-right: 20px;
  }
  @media (max-width: 767px) {
    padding-right: 0;
  }
  .title {
    margin-bottom: 20px;
    width: 435px;
    @media (min-width: 768px) and (max-width: 1279px) {
      width: 235px;
    }
  }
}
.char_sns {
  display: flex;
  align-items: center;
  margin-top: 20px;
  @media (max-width: 767px) {
    box-sizing: border-box;
    padding: 0 20px;
    width: 100%;
  }
  .text {
    font-size: 32px;
    font-weight: bold;
    color: #fff;
    @media (min-width: 768px) and (max-width: 1279px) {
      font-size: 28px;
    }
    @media (max-width: 767px) {
      font-size: 16px;
    }
  }
  .sns {
    margin-left: auto;
    width: 48px;
    @media (min-width: 768px) and (max-width: 1279px) {
      width: 38px;
    }
    @media (max-width: 767px) {
      width: 24px;
    }
  }
  .sns2 {
    margin-left: 20px;
    width: 48px;
    @media (min-width: 768px) and (max-width: 1279px) {
      width: 38px;
    }
    @media (max-width: 767px) {
      width: 24px;
      margin-left: 10px;
    }
  }
}
.pc-only {
  display: flex;
  @media (max-width: 767px) {
    display: none;
  }
}
.mobile-only {
  display: none;
  @media (max-width: 767px) {
    display: block;
  }
}
.ytube {
  flex: none;
  position: relative;
  width: 100%;
  .video {
    position: relative;
    z-index: 10;
    width: 100%;
  }
  iframe {
    height: 90%;
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
  }
}
</style>
