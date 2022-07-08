<template>
  <div class="cursos">
    
    <div v-if="loading">
      <PageLoading />
    </div>

    <transition name="fade">
      <div class="grid">
        <div v-if="api">
          <h1>{{ api.titulo }}</h1>
          {{ api.descricao }} 
                  
        </div>

        <div class="aulas">
          <ul>
            <li v-for="curso in api.cursos" :key="curso">
              <router-link :to="{name: 'curso', params: {curso: curso.id}}">
                <h2>
                  {{ curso.nome }} - {{ curso.totalAulas }} aulas |
                  {{ curso.horas }} horas
                </h2>
              </router-link>
              <p>
                {{curso.descricao}}
              </p>
            </li>
          </ul>
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
import fetchData from "@/mixins/fetchData.js";

export default {
  name: "Cursos",
  mixins: [fetchData],
  created() {
    this.fetchData("/cursos");
  },
};
</script>

<style scoped>
h1 {
  margin: 25px 0;
  font-size: 2.5rem;
}
.grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 40px;
}
ul {
  padding: 0;
  list-style: none;
  margin: 25px 0;
}
ul h2,
ul p {
  margin-bottom: 20px;
}
ul h2 {
  font-size: 1.8rem;
}
ul a {
  text-decoration: none;
  color: black;
}
</style>
