<template>
  <section class="section3">
    <div class="section3-box">
      <div class="section3-intro">
        <div class="card-content pc-only">
          <div class="card-box">
            <div class="card-box-f">
              <img :src="panelMember" class="section3-panel-member" />
            </div>
            <div class="card-box-b">
              <img :src="panelMemberBack" class="section3-panel-member" />
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
  <div class="section3-panel">
    <img
      :src="panel"
      class="section3-panel-member pc-only wow fadeInUp"
      data-wow-duration="1s"
      data-wow-delay="0.5s"
    />
    <img
      :src="panelMo"
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
      panelMember: require("@/assets/image/section3/flip_card_f.png"),
      panelMemberBack: require("@/assets/image/section3/flip_card_b.png"),
      panel: require("@/assets/image/section3/img_character_v2.png"),
      panelMo: require("@/assets/image/section3/img_character_mo_v2.png"),
    });
    return {
      ...toRefs(state),
    };
  },
};
</script>

<style scoped></style>
