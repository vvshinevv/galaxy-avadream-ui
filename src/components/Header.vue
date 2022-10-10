<template>
  <header class="header">
    <a
      href="http://broadcast.tvchosun.com/broadcast/program/2/C202200147.cstv"
      class="pc-only"
      target="_blank"
    >
      <img :src="logoUrl2" class="logo-chosun" />
    </a>
    <router-link class="header-logo" to="/">
      <img :src="logoUrl" />
    </router-link>
    <a href="https://galaxyava.com/" target="_blank" class="pc-only"
      ><img :src="logoUrl3" class="logo-world"
    /></a>
    <MenuLayer />
  </header>
</template>

<script>
import { reactive, toRefs } from "vue";
import MenuLayer from "@/components/MenuLayer";
export default {
  name: "Header",
  components: { MenuLayer },
  setup() {
    const state = reactive({
      logoUrl: require("@/assets/image/logo_v2.png"),
      logoUrl2: require("@/assets/image/logo_chosun_v2.png"),
      logoUrl3: require("@/assets/image/logo_world.png"),
    });
    return {
      ...toRefs(state),
    };
  },
};
</script>
