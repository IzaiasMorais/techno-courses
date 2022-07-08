<template>
  <div id="app">
    <TheHeader></TheHeader>

    <div class="router-container">
      <transition name="fade">
        <router-view></router-view>
      </transition>
    </div>
  </div>
</template>

<script>
import TheHeader from "@/components/TheHeader.vue";

export default {
  components: {
    TheHeader,
  },
};
</script>

<style>
* {
  margin: 0;
  font-family: "Sen";
}
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  /* color: #42b983; */
}
.router-container {
  max-width: 1000px;
  margin: 0 auto;
  padding: 20px;
}
.fade-enter {
  transition: 0;
  transform: translate3d(-20px, 0, 0);
}
.fade-enter-active {
  transition: all .2s;
}
</style>
