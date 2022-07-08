<template>
  <div class="curso">
    <div v-if="loading">
      <PageLoading />
    </div>

    <transition name="fade">
      <div v-if="api">
        <h1>{{ api.nome }}</h1>
        <p>{{ api.descricao }}</p>
        <h1>Aulas</h1>
        <ul>
          <li v-for="aula in api.aulas" :key="aula.id">
            <router-link :to="{ name: 'aula', params: { aula: aula.id } }">
              {{ aula.nome }}
            </router-link>
          </li>
        </ul>
      </div>
    </transition>

    <transition name="fade">
      <div class="aula" v-if="api">
        <router-view></router-view>
      </div>
    </transition>
  </div>
</template>

<script>
import fetchData from "@/mixins/fetchData.js";

export default {
  name: "curso",
  props: ["curso"],
  mixins: [fetchData],
  created() {
    this.fetchData(`/curso/${this.curso}`);
  },
};
</script>

<style scoped>
ul {
  list-style: none;
  padding: 0;
}
h1,
ul,
p {
  margin-bottom: 20px;
}
p {
  font-size: 1.3rem;
}
ul a {
  text-decoration: none;
  color: black;
}
ul li a {
  font-size: 1.3rem;
  font-weight: bold;
  margin-bottom: 20px;
  display: block;
  box-shadow: 0.2px 1px 1px 1px rgba(0, 0, 0, 0.139);
  padding: 25px 20px;
  border-radius: 4px;   
}
ul li a.router-link-active {
  background: #4b8 !important;
  color: white;
}
ul li a:hover {
  animation: ease 0.3s;
}
.curso {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 40px;
}
@keyframes ease {
  from {
    transform: translate3d(0, 0, 0);
  }
  to {
    transform: translate3d(0, -5px, 0);
  }
}
</style>
