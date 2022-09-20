<template>
  <section class="section3">
    <div class="section3-box">
      <div class="section3-intro">
        <div class="card-content">
          <div class="card-box wow flip"
               data-wow-duration="1s"
               data-wow-delay="0.5s">
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
    <div class="section3-panel-box pc-only">
      <img
        :src="panel"
        class="section3-panel-member wow fadeInUp"
        data-wow-duration="1s"
        data-wow-delay="0.5s"
      />
<!--      <ul class="section3-panel-list">-->
<!--        <li>-->
<!--          <img-->
<!--            :src="cardPannel"-->
<!--            class="section3-panel-member wow fadeInUp"-->
<!--            data-wow-duration="1s"-->
<!--            data-wow-delay="0.5s"-->
<!--          />-->
<!--        </li>-->
<!--        <li>-->
<!--          <img-->
<!--            :src="cardPannel2"-->
<!--            class="section3-panel-member wow fadeInUp"-->
<!--            data-wow-duration="1s"-->
<!--            data-wow-delay="0.5s"-->
<!--          />-->
<!--        </li>-->
<!--        <li>-->
<!--          <img-->
<!--            :src="cardPannel3"-->
<!--            class="section3-panel-member wow fadeInUp"-->
<!--            data-wow-duration="1s"-->
<!--            data-wow-delay="0.5s"-->
<!--          />-->
<!--        </li>-->
<!--        <li>-->
<!--          <img-->
<!--            :src="cardPannel4"-->
<!--            class="section3-panel-member wow fadeInUp"-->
<!--            data-wow-duration="1s"-->
<!--            data-wow-delay="0.5s"-->
<!--          />-->
<!--        </li>-->
<!--      </ul>-->
    </div>
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
      cardPannel: require("@/assets/image/section3/pannel1.png"),
      cardPannel2: require("@/assets/image/section3/pannel2.png"),
      cardPannel3: require("@/assets/image/section3/pannel3.png"),
      cardPannel4: require("@/assets/image/section3/pannel4.png"),
    });
    return {
      ...toRefs(state),
    };
  },
};
</script>

<style scoped lang="scss">
@media (max-width: 560px) {
  .card-content {
    height: 340px;
  }
}
@media (max-width: 440px) {
  .card-content {
    height: 300px;
  }
}
.section3-panel-box {
  position: relative;
}
.section3-panel-list {
  display: flex;
  max-width: 1459px;
  position: absolute;
  top: 440px;
  left: 212px;
  bottom: 0;
  right: 190px;
  align-items: flex-start;
  li {
    &:first-child {
      margin-left: 0;
    }
    &:last-child {
      margin-right: 0;
    }
    flex: 1;
    margin: 0 21px;
  }
  img {
    width: 100%;
  }
}
</style>
