<template>
  <div class="home">
    <div v-if="loading">
      <PageLoading />
    </div>

    <transition name="fade">
      <div v-if="api">
        <h1>Sobre a {{ api.titulo }}</h1>
        <p>{{ api.descricao }}</p>
        <router-link class="button" to="/cursos">Cursos</router-link>
        <h1 class="avaliacoes">Avaliações</h1>
        <ul>
          <li v-for="avaliacao in api.avaliacoes">
            <p>{{ avaliacao.nome }}</p>
            <p>"{{ avaliacao.descricao }}"</p>
          </li>
        </ul>
      </div>
    </transition>

    <transition name="fade">
      <div v-if="api">
        <img src="@/assets/aprender.png" alt="" />
      </div>
    </transition>
  </div>
</template>

<script>
import fetchData from "@/mixins/fetchData.js";

export default {
  name: "Home",
  mixins: [fetchData],
  created() {
    this.fetchData("/home");
  },
};
</script>

<style scoped>
h1 {
  margin: 25px 0;
  font-weight: bold;
  font-size: 2.5rem;
}
img {
  max-width: 100%;
}
.home {
  display: grid;
  grid-template-columns: 1fr 1fr;
}
ul {
  list-style: none;
  padding: 0;
}
.button {
  background: #4b8;
  border: none;
  padding: 15px 45px;
  width: fit-content;
  border-radius: 4px;
  cursor: pointer;
  font-size: 1rem;
  color: white;
  display: block;
  text-decoration: none;
  margin: 40px 0;
  box-shadow: 0px 4px 0px rgba(0, 0, 0, 0.1);
}
.button:hover {
  background: rgb(57, 159, 115);
  animation: ease 0.3s forwards;
}
.avaliacoes {
  font-size: 2rem;
}
ul li,
ul p {
  margin-bottom: 20px;
}
ul li {
  border-radius: 4px;
  padding: 10px;
  box-shadow: 0.2px 1px 1px 1px rgba(0, 0, 0, 0.139);
}
ul li:hover {
  animation: ease 0.3s forwards;
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
