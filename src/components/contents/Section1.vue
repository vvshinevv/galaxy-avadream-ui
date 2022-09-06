<template>
  <section class="section1" >
    <h1 class="section1-title wow fadeInUp" data-wow-duration="1s" data-wow-delay="0.5s">아바드림</h1>
  </section>
</template>

<script>
import WOW from 'wowjs';
export default {
  name: "Section1",
    mounted(){
        let wow = new WOW.WOW({
            boxClass: 'wow',
            animateClass: 'animated',
            offset: 0,
            mobile: true,
            live: true
        });
        wow.init();
    }
};
</script>

<style scoped></style>
