<template>
  <footer class="footer">
    <div class="footer-box">
        <div class="footer-box-link">
            <a href="#">
                <img :src="footerLink" />
            </a>
            <a href="#">
                <img :src="footerLink2" />
            </a>
            <a href="#">
                <img :src="footerLink3" />
            </a>
        </div>
        <ul class="footer-link-text">
            <li>
                갤럭시유니버스<br class="mobile-only"/> 사이트 가기
            </li>
            <li>
                갤럭시코퍼레이션<br class="mobile-only"/> 사이트 가기
            </li>
            <li>
                개인정보처리방침
            </li>
        </ul>
        <p class="footer-bottom-text">
            사업자명 : 주식회사 페르소나스페이스  사업자 등록번호 : 380-86-02330  대표자명 : 최용호<br/>
            CONTACT : jin@galaxyuniverse.ai
        </p>
    </div>
  </footer>
</template>

<script>
import {reactive, toRefs} from "vue";
import {Autoplay, Navigation} from "swiper";

export default {
  name: "Footer",
    setup() {
        const state = reactive({
            footerLink: require("@/assets/image/footer_link.png"),
            footerLink2: require("@/assets/image/footer_link2.png"),
            footerLink3: require("@/assets/image/footer_link3.png"),
        });
        return {
            ...toRefs(state),
        };
    },
};
</script>

<style scoped lang="scss">

</style>
