<template>
  <section class="section3">
    <div class="section3-box">
      <div class="section3-intro">
        <img
          :src="mcUrl"
          class="section3-intro-mc pc-only wow fadeInUp"
          data-wow-duration="1s"
          data-wow-delay="0.5s"
        />
        <img
          :src="mcUrl2"
          class="section3-intro-mc mobile-only wow fadeInUp"
          data-wow-duration="1s"
          data-wow-delay="0.5s"
        />
      </div>
    </div>
  </section>
  <div class="section3-panel">
    <!--          <img :src="titleUrl2" class="section3-panel-title" />-->
    <img
      :src="panelMember"
      class="section3-panel-member pc-only wow fadeInUp"
      data-wow-duration="1s"
      data-wow-delay="0.5s"
    />
    <img
      :src="panelMemberMo"
      class="section3-panel-member mobile-only wow fadeInUp"
      data-wow-duration="1s"
      data-wow-delay="0.5s"
    />
  </div>
</template>

<script>
import WOW from "wowjs";
import { reactive, toRefs } from "vue";

export default {
  name: "Section3",
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
      mcUrl: require("@/assets/image/section3/img_mc_v2.png"),
      mcUrl2: require("@/assets/image/section3/img_mc_mo_v2.png"),
      titleUrl2: require("@/assets/image/section3/img_title.png"),
      introTitle: require("@/assets/image/section3/img_intro_title2.png"),
      introTitleText: require("@/assets/image/section3/img_intro2.png"),
      introTitleTextMo: require("@/assets/image/section3/img_intro2_mo.png"),
      introTitle2: require("@/assets/image/section3/img_intro_title.png"),
      introTitleText2: require("@/assets/image/section3/img_intro.png"),
      introTitleText2Mo: require("@/assets/image/section3/img_intro_mo.png"),
      panelMember: require("@/assets/image/section3/img_character_v2.png"),
      panelMemberMo: require("@/assets/image/section3/img_character_mo_v2.png"),
    });
    return {
      ...toRefs(state),
    };
  },
};
</script>

<style scoped></style>
