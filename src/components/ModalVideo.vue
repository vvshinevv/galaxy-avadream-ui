<template>
  <Modal
    :visible="visible"
    @update:visible="$emit('update:visible', false)"
    innerClass="modal-image"
    :showClose="true"
    :dimClose="true"
  >
    <video controls v-if="movieUrl.url1">
      <source :src="movieUrl.url1" type="video/webm" />
      <source :src="movieUrl.url2" type="video/mp4" />
    </video>
      <iframe v-if="movieUrl.youtubeLink"
          id="videoYtube"
          width="100%"
              height="70%"
          style="object-fit: contain"
          :src="movieUrl.youtubeLink"
          title="YouTube video player"
          frameborder="0"
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
          allowfullscreen
      ></iframe>
  </Modal>
</template>

<script>
import Modal from "@/components/Modal";
import {computed, reactive, toRefs} from "vue";
export default {
  name: "ModalVideo",
  components: { Modal },
  props: {
    visible: {
      type: Boolean,
      default: false,
    },
      movieUrl: {
      type: Object,
      default: () => {
        return {};
      },
    },
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
}
video {
  width: calc(100% - 480px);
  height: auto;
  @media (min-width: 768px) and (max-width: 1279px) {
    width: calc(100% - 140px);
  }
  @media (max-width: 767px) {
    width: 100%;
  }
}
iframe{
    @media (min-width: 768px) and (max-width: 1279px) {
        height: 60%
    }
    @media (max-width: 767px) {
        height: 28%
    }
}
</style>
