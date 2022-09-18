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
        <img :src="char1" />
      </div>
      <div class="card-char-video">
        <img :src="charTitle1" class="title" />
        <img :src="charVideo1" class="video" />
        <div class="char_sns">
          <p class="text">동보희 이야기 보러가기</p>
          <img :src="sns1" class="sns" />
          <img :src="sns2" class="sns2" />
        </div>
      </div>
    </div>
    <div class="card-char-box mobile-only">
      <div class="card-char-img">
        <img :src="char1Mo" />
      </div>
      <div class="card-char-video">
        <img :src="charVideo1" class="video" />
        <div class="char_sns">
          <p class="text">동보희 이야기 보러가기</p>
          <img :src="sns1" class="sns" />
          <img :src="sns2" class="sns2" />
        </div>
      </div>
    </div>
  </Modal>
</template>

<script>
import Modal from "@/components/Modal";
import { reactive, toRefs } from "vue";
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
  },
  setup() {
    const state = reactive({
      imgUrl: require("@/assets/image/section5/img2.webm"),
      imgUrl2: require("@/assets/image/section5/img2.webm"),
      char1: require("@/assets/image/pc_card/char1.png"),
      char1Mo: require("@/assets/image/mo_card/char1_m.png"),
      charTitle1: require("@/assets/image/pc_card/charTitle1.png"),
      charVideo1: require("@/assets/image/pc_card/charVideo1.png"),
      sns1: require("@/assets/image/pc_card/ico_u.png"),
      sns2: require("@/assets/image/pc_card/ico_in.png"),
    });
    return {
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
  img {
    width: 100%;
  }
}
.card-char-img {
  width: 40%;
  display: flex;
  align-items: flex-end;
  @media (max-width: 767px) {
    margin: 0 auto;
    width: 60%;
  }
}
.card-char-video {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: center;
  .title {
    margin-bottom: 20px;
    width: 435px;
    @media (min-width: 768px) and (max-width: 1279px) {
      width: 235px;
    }
  }
  .video {
    width: calc(100% - 80px);
    margin-bottom: 20px;
    @media (min-width: 768px) and (max-width: 1279px) {
      width: calc(100% - 20px);
    }
    @media (max-width: 767px) {
      width: 100%;
    }
  }
}
.char_sns {
  width: calc(100% - 80px);
  display: flex;
  align-items: center;
  @media (min-width: 768px) and (max-width: 1279px) {
    width: calc(100% - 20px);
  }
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
    }
  }
}
.pc-only {
  display: block;
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
</style>
