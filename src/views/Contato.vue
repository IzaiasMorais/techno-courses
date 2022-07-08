<template>
  <div class="contato">
    <div v-if="loading">
      <PageLoading />
    </div>

    <transition name="fade">
      <div v-if="api">
        <h1>Contato</h1>
        <p>{{ api.descricao }}</p>
        <ul>
          <li v-for="(contat, key) in api.contato">
            <span>{{ key }}:</span> {{ contat }}
          </li>
        </ul>
      </div>
    </transition>
  </div>
</template>

<script>
import fetchData from "@/mixins/fetchData.js";

export default {
  name: "Contato",
  mixins: [fetchData],
  created() {
    this.fetchData("/contato");
  },
};
</script>

<style scoped>
h1 {
  margin: 25px 0;
  font-size: 2.5rem;
}
p {
  margin: 0 0 20px 0;
  font-size: 1.2rem;
}
ul {
  list-style: none;
  padding: 0;
  font-size: 1.2rem;
}
span {
  font-weight: bold;
  text-transform: capitalize;
}
</style>
