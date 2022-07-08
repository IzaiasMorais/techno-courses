<template>
  <header>
    <nav>
      <div class="nav-container">
        <router-link to="/" class="logo">Techno</router-link>
        <ul>
          <router-link to="/cursos">Cursos</router-link>
          <router-link to="/contato">Contato</router-link>
        </ul>
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  name: "TheHeader",
};
</script>

<style scoped>
  nav {
    background: #2c3e50;
    height: 88px;    
  }
  .nav-container {
    display: flex;   
    align-items: center;
    height: 100%;
    max-width: 1000px;
    margin: 0 auto;
    justify-content: space-between;
  }
  .nav-container  a {
    font-weight: 600;
    text-decoration: none;
    color: white;
    font-size: 1.3rem;
    padding: 30px 0;
    transition: color 0.1s;
  }
  .nav-container  a:hover {
    color: #4b8;
  }
  .nav-container ul {
    display: flex;
    gap: 30px;
    margin: 0;
    padding: 0;
  }
  .nav-container a.router-link-active {
    color: #42b983;
  }
  .logo {
    color: white !important;
    font-size: 1.6rem !important;
  }
</style>
