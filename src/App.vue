<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <header>
    <div class="header">
      <a href="https://www.afocatregioncentro.pe/">
        <img class="logo my-5" alt="logo" src="./assets/logo-afocat-001.svg" />
      </a>
    </div>
  </header>
  <div class="contenedor w-1/2 my-5 mx-auto py-5 px-10 text-white">
    <h1 class="text-4xl mb-5 font-bold">Consulte su vigencia</h1>
    <hr class="border-t-2 border-green-500 mb-5 w-3/4 mx-auto" />
    <form id="consultaForm" class="flex flex-col">
      <label for="placa" class="label mb-2 text-left mx-2">Ingrese su placa</label>
      <input
        type="text"
        id="placa"
        name="placa"
        placeholder="Ej.(V1V123)"
        class="mb-4 bg-transparent text-white"
      />
      <input type="submit" value="Consultar Vigencia" class="submit px-4 py-2 text-white" />
    </form>
  </div>
  <div class="wrapper">
    <nav>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/about">About</RouterLink>
    </nav>
  </div>
  <RouterView />
</template>

<style>
.header {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
}

.logo {
  width: 320px;
  height: 100%;
}
.contenedor {
  background-color: #061943;
  border-radius: 10px;
}
.submit {
  background-color: #00906f;
}
.label {
  color: #8397bc;
  cursor: pointer;
}
input {
  border: 1px solid #8397bc;
  padding: 5px;
  color: #8397bc;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
}
</style>
