<template>
  <div id="app" class="font-quick bg-gray-100" ref="clock">
    <div id="nav" class="py-2 px-4">
      <router-link to="/">Home</router-link>
    </div>
    <router-view />
    <div class="cover" ref="cover"></div>
  </div>
</template>

<script>
import gsap from "gsap";
export default {
  mounted() {
    gsap.fromTo(
      this.$refs.cover,
      {
        opacity: 1,
      },
      {
        opacity: 0,
        duration: 3,
        y: "-101%",
      }
    );
    gsap.fromTo(
      this.$refs.clock,
      {
        opacity: 0,
        y: "100",
      },
      {
        opacity: 1,
        duration: 1,
        delay: 1,
        y: "0",
      }
    );
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Quicksand&display=swap");
body {
  font-family: "Quicksand", sans-serif;
  background-color: #f4f4f5;
}
.cover {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  background-color: grey;
}
</style>
