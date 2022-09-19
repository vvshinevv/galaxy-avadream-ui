<template>
  <Modal
    :visible="visible"
    @update:visible="$emit('update:visible', false)"
    innerClass="modal-image"
    :showClose="true"
    :dimClose="true"
  >
    <div class="modal-image-box">
      <img :src="imgUrl" class="bg pc-only" />
      <img :src="imgUrlMo" class="bg mobile-only" />
    </div>
  </Modal>
</template>

<script>
import Modal from "@/components/Modal";
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
    imgUrlMo: {
      type: String,
      default: "",
    },
  },
};
</script>

<style scoped lang="scss">
:deep(.modal-image){
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;
  @media (max-width: 767px){
    width: auto;
    height: 100%;
  }
}
.bg{
  width: 100%;
  height: 100%;

  @media (max-width: 767px){
    width: auto;
    height: 100vh;
  }
}
</style>
