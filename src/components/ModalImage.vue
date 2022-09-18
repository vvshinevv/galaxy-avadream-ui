<template>
  <Modal
    :visible="visible"
    @update:visible="$emit('update:visible', false)"
    innerClass="modal-image"
    :showClose="true"
    :dimClose="true"
  >
      <video
          controls
      >
          <source :src="imgUrl" type="video/webm" />
          <source :src="imgUrl2" type="video/mp4" />
      </video>
  </Modal>
</template>

<script>
import Modal from "@/components/Modal";
import {reactive, toRefs} from "vue";
export default {
  name: "ModalImage",
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
            imgUrl2: require("@/assets/image/section5/img2.mp4")
        });
        return {
            ...toRefs(state),
        };
    },
};
</script>

<style scoped lang="scss">
:deep(.modal-image){
    max-width: 1920px;
    max-height: 1080px;
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content:center;
}
video{
    width: calc(100% - 480px);
    height: auto;
    @media (min-width: 768px) and (max-width: 1279px) {
        width: calc(100% - 140px);
    }
    @media (max-width: 767px) {
        width: 100%;
    }
}
</style>
