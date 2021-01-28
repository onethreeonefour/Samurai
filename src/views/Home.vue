<template>
  <div v-if="!isMobile()">
    <Hero />
  </div>
  <div v-else>
    <div class="mobile-view">
      <h2>
        This is a desktop experience only. <br /><br />
        Please try this website on a desktop or laptop. Cheers!
      </h2>
    </div>
  </div>
</template>

<script>
import Hero from "../components/Hero";

export default {
  components: {
    Hero,
  },
  methods: {
    isMobile() {
      if (/Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(navigator.userAgent)) {
        return true;
      } else {
        return false;
      }
    },
  },
};
</script>
<style lang="scss" scoped>
.mobile-view {
  display: flex;
  height: 100vh;
  align-items: center;
  justify-content: center;
  background: #000;
  color: white;
  font-size: 1rem;
  padding: 2rem;
}
</style>
