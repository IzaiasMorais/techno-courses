<template>
  <div>
    <div v-if="loading">
      <PageLoading />
    </div>

    <transition name="fade">
      <div v-if="api">
        <h1>{{ api.nome }}</h1>
        <div class="video">
          <iframe
            width="560"
            height="315"
            :src="`https://www.youtube.com/embed/${api.youtube}`"
            title="YouTube video player"
            frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
            allowfullscreen
          ></iframe>
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
import fetchData from "@/mixins/fetchData.js";

export default {
  name: "aula",
  props: ["aula"],
  mixins: [fetchData],
  created() {
    this.fetchData(`/aula/${this.aula}`);
  },
  beforeRouteUpdate(to, from, next) {
    this.fetchData(`/aula/${to.params.aula}`);
    next();
  },
};
</script>

<style scoped>
li {
  text-decoration: none;
  color: black;
}
h1 {
  margin: 0 0 20px 0;
}
.video {
  position: relative;
  padding-bottom: 56.24%;
}
iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
</style>
