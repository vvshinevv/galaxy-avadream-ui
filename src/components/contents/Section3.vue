<template>
  <section class="section3">
    <div class="section3-intro">
      <img :src="titleUrl" class="section3-intro-title" />
      <img :src="characterUrl" class="section3-intro-char" />
      <div class="section3-intro-box">
        <div class="left">
          <img :src="introTitle" class="title" />
          <img :src="introTitleText" class="pc-only" />
          <img :src="introTitleTextMo" class="mobile-only" />
        </div>
        <div class="right">
          <img :src="introTitle2" class="title" />
          <img :src="introTitleText2" class="pc-only" />
          <img :src="introTitleText2Mo" class="mobile-only" />
        </div>
      </div>
      <div class="section3-panel">
        <img :src="titleUrl2" class="section3-panel-title" />
        <img :src="panelMember" class="section3-panel-member pc-only" />
        <img :src="panelMemberMo" class="section3-panel-member mobile-only" />
      </div>
    </div>
  </section>
</template>

<script>
import { reactive, toRefs } from "vue";

export default {
  name: "Section3",
  setup() {
    const state = reactive({
      titleUrl: require("@/assets/image/section3/img_mc_title.png"),
      titleUrl2: require("@/assets/image/section3/img_title.png"),
      characterUrl: require("@/assets/image/section3/img_mc.png"),
      introTitle: require("@/assets/image/section3/img_intro_title2.png"),
      introTitleText: require("@/assets/image/section3/img_intro2.png"),
      introTitleTextMo: require("@/assets/image/section3/img_intro2_mo.png"),
      introTitle2: require("@/assets/image/section3/img_intro_title.png"),
      introTitleText2: require("@/assets/image/section3/img_intro.png"),
      introTitleText2Mo: require("@/assets/image/section3/img_intro_mo.png"),
      panelMember: require("@/assets/image/section3/img_character.png"),
      panelMemberMo: require("@/assets/image/section3/img_character_mo.png"),
    });
    return {
      ...toRefs(state),
    };
  },
};
</script>

<style scoped></style>
