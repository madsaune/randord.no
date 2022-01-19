<template>
  <Header />

  <main>
    <router-view />
  </main>

  <Footer />
</template>

<script>
import Header from "@/components/Header.vue";
import Footer from "@/components/Footer.vue";

export default {
  components: { Footer, Header },
};
</script>
