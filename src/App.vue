<template>
  <div id="app">
    <div class="fixed-top">
      <Navbar />
    </div>
    <router-view/>
    <Footer />
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";
import Footer from "@/components/Footer.vue";
export default {
  components : {
    Navbar,
    Footer,
  }
}
</script>

<style scoped>

</style>
