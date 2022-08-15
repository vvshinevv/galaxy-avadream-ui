<template>
  <header class="header">
    <router-link class="header-logo" to="/">
      <img :src="logoUrl" />
    </router-link>
    <img :src="logoUrl2" class="logo-chosun" />
  </header>
</template>

<script>
import { reactive, toRefs } from "vue";
export default {
  name: "Header",
  setup() {
    const state = reactive({
      logoUrl: require("@/assets/image/logo.png"),
      logoUrl2: require("@/assets/image/logo_chosun.png"),
    });
    return {
      ...toRefs(state),
    };
  },
};
</script>
