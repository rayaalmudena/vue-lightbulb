<script setup>
import LightBulb from './components/LightBulb.vue';
</script>

<script>
export default {
  data() {
    return {
      totalLights: 3
    }
  }
}
</script>


<template>
  
  <h1 v-if="totalLights != 0">¡Enciende todas las luces!</h1>
  <h1 v-else>¡Todas encendidas!</h1>

  <main class="bulbs">
    <!-- escuchar al custom event y ejecutar una función. De momento la función que haga un console.log informando de que se ha encendido.
    Cada vez que ejecuta la función decrementa en 1 el número de bombillas que faltan por encender. 
    Mostrar un mensaje de que todas las bombillas estan encedidas solo cuando totalLight==0  -->
    <light-bulb @switchedOn="totalLights--" necessaryClicks="1"></light-bulb>
    <light-bulb @switchedOn="totalLights--" necessaryClicks="3"></light-bulb>
    <light-bulb @switchedOn="totalLights--" necessaryClicks="2"></light-bulb>

  </main>
</template>

<style>
@import './assets/base.css';

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;

  font-weight: normal;
}

.bulbs {
  display: flex;
}

header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

a,
.green {
  text-decoration: none;
  color: hsla(160, 100%, 37%, 1);
  transition: 0.4s;
}

@media (hover: hover) {
  a:hover {
    background-color: hsla(160, 100%, 37%, 0.2);
  }
}

@media (min-width: 1024px) {
  body {
    display: flex;
  }

  #app {
    padding: 0 2rem;
  }

  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  .logo {
    margin: 0 2rem 0 0;
  }
}
</style>
