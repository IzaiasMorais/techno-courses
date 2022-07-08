# ROUTER

<router-view></router-view>

<router-link></router-link>

# DYNAMIC ROUTER

{
  path: '/cursos/:curso',
  component: Cursos,
  props: true
}

# NAVIGATION GUARDS

`// main.js router global`
`router.beforeEach((to, from, next) => {`
  // Código antes do router entrar
  `next();`
});

`router.afterEach((to, from) = {`
  // Código após do router entrar
});

## LOCALS
> will only happen when we enter in the component

export default new Router({
  routes: [
    {
      path: "/",
      `component: Home,`
      beforeEnter: (to, from, next) => {
        // Código para ser ativado
      }
    }
  ],
});

<script>
export default {
  beforeRouteEnter(to, from, next) {
    // Antes de entrar no router, não tem acesso ao this
  },
  beforeRouteUpdate(to, from, next) {
    // Quando um router já ativo é atualizado
  },
  beforeRouteLeave(to, from, next) {
    // Antes de sair do router
    // next("/") é possível passar outros caminhos para o next()
    `WE CAN USE TO MAKE A CONTS CONFIRM = CONFIRM... AND VERIFY BY TRUE OR FALSE`
  }
};
</script>

# TRANSITIONS

`Transition need :key='name' when it covers routers views that look the same `
<transion>
  <router-view>
</transition>

# FETCH

# +ROUTER

scrollBehavior(to, from, savedPosition) {
  return {
    x: 0,
    y: 0
  }

    // return window.scrollTo ({top: 0, behavior: 'smooth'})
}

# LAZY LOADING

`instead of using import Route.vue from '../../Route.vue'`
use 
const Curso = () => import(/* webpackChunkName: "curso" */ './views/Curso.vue');

# 

# 

# 

# 