<template>
  <main class="ava-wrap">
    <Header />
    <Section1></Section1>
    <Section2></Section2>
    <Section3></Section3>
    <Section4></Section4>
    <Section5></Section5>
    <Section6></Section6>
    <Section7></Section7>
    <Footer />
  </main>
</template>

<script>
import Header from "@/components/Header";
import Footer from "@/components/Footer";
import Section1 from "@/components/contents/Section1";
import Section2 from "@/components/contents/Section2";
import Section3 from "@/components/contents/Section3";
import Section4 from "@/components/contents/Section4";
import Section5 from "@/components/contents/Section5";
import Section6 from "@/components/contents/Section6";
import Section7 from "@/components/contents/Section7";

export default {
  name: "Main.vue",
  components: {
    Section7,
    Section6,
    Section5,
    Section4,
    Section2,
    Footer,
    Header,
    Section1,
    Section3,
  },
};
</script>

<style scoped></style>
