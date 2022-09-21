<template>
  <section class="section3">
    <div class="section3-box">
      <div class="section3-intro">
        <div class="card-content">
          <div class="card-box"
               id="flipCard"
          >
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
    <div class="section3-panel-box" id="flipCardPanel">
      <img
        :src="panel"
        class="section3-panel-member pc-only"
      />
      <img
          :src="panelMo"
          class="section3-panel-member mobile-only"
      />
      <ul class="section3-panel-list">
        <li>
          <img
            :src="cardPannel"
            class="section3-panel-member"
          />
          <img
              :src="cardPannel2"
              class="section3-panel-member"
          />
        </li>
        <li>
          <img
            :src="cardPannel3"
            class="section3-panel-member"
          />
          <img
              :src="cardPannel4"
              class="section3-panel-member"
          />
        </li>
        <li>
          <img
            :src="cardPannel5"
            class="section3-panel-member"
          />
          <img
              :src="cardPannel6"
              class="section3-panel-member"
          />
        </li>
        <li>
          <img
            :src="cardPannel7"
            class="section3-panel-member"
          />
          <img
              :src="cardPannel8"
              class="section3-panel-member"
          />
        </li>
      </ul>
    </div>
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

    window.onscroll = () => {
      const windowWidth = window.innerWidth;
      const top = window.pageYOffset || document.documentElement.scrollTop;
      const flipCard = document.getElementById('flipCard');
      const flipCardPanelPc = document.getElementById('flipCardPanel');
      if(windowWidth > 1280){
        flipCardPanelPc.classList.remove("form-fixed");
        flipCard.classList.remove("form-fixed");
        if (top > 4900 ) {
          flipCard.classList.add("form-fixed");
          if(top > 6200){
            flipCardPanelPc.classList.add("form-fixed");
          }
        }

      } else if(windowWidth > 768){
        flipCardPanelPc.classList.remove("form-fixed");
        flipCard.classList.remove("form-fixed");
        if (top > 3500) {
          flipCard.classList.add("form-fixed");
          if(top > 4000){
            flipCardPanelPc.classList.add("form-fixed");
          }
        }
      }else{
        flipCardPanelPc.classList.remove("form-fixed");
        flipCard.classList.remove("form-fixed");
        if (top > 1800) {
          flipCard.classList.add("form-fixed");
          if(top > 2400){
            flipCardPanelPc.classList.add("form-fixed");
          }
        }
      }
    }
  },
  setup() {
    const state = reactive({
      mcUrl: require("@/assets/image/section3/img_mc_v2.png"),
      mcUrl2: require("@/assets/image/section3/img_mc_mo_v2.png"),
      panelMember: require("@/assets/image/section3/flip_card_f.png"),
      panelMemberBack: require("@/assets/image/section3/flip_card_b.png"),
      panel: require("@/assets/image/section3/img_character_v3.png"),
      panelMo: require("@/assets/image/section3/img_character_mo_v3.png"),
      cardPannel: require("@/assets/image/section3/cardPanel1.png"),
      cardPannel2: require("@/assets/image/section3/cardPanel6.png"),
      cardPannel3: require("@/assets/image/section3/cardPanel2.png"),
      cardPannel4: require("@/assets/image/section3/cardPanel3.png"),
      cardPannel5: require("@/assets/image/section3/cardPanel7.png"),
      cardPannel6: require("@/assets/image/section3/cardPanel8.png"),
      cardPannel7: require("@/assets/image/section3/cardPanel4.png"),
      cardPannel8: require("@/assets/image/section3/cardPanel5.png"),
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
  top: 420px;
  left: 212px;
  bottom: 0;
  right: 190px;
  align-items: flex-start;

  li {
    position: relative;
    flex: 1;
    margin: 0 21px;
    transform-style: preserve-3d;
    @at-root .form-fixed li{
      animation: 1s 1 alternate rotate;
      animation-fill-mode: forwards;
    }
    &:first-child {
      margin-left: 0;
    }
    &:last-child {
      margin-right: 0;
    }

    img:first-child{
      position: absolute;
      width: 100%;
      backface-visibility: hidden;
      z-index:1;
    }
    img:last-child{
      position: absolute;
      width: 100%;
      backface-visibility: hidden;
      transform: rotateY(180deg);
    }
  }
  img {
    width: 100%;
  }
}
@keyframes rotate {
  from {
    transform: rotateY(0);
  }

  to {
    transform: rotateY(180deg);
  }
}
@media (min-width: 768px) and (max-width: 1279px) {
  .section3-panel-list{
    top: 31%;
    left: 12%;
    right: 12%;
    li{
      margin: 0 15px;
    }
  }
}
@media (max-width: 768px) {
  .section3-panel-list{
    top: 32%;
    left: 14%;
    right: 14%;
    li{
      margin: 0 10px;
    }
  }
}
</style>
