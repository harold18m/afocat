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
    <h1 class="text-4xl mb-5 font-bold">Consulte Su Vigencia</h1>
    <hr class="border-t-2 border-green-500 mb-5 w-3/4 mx-auto" />
    <form v-if="!submitted" id="consultaForm" @submit.prevent="submitForm" class="flex flex-col">
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
    <div v-else>
      <h2>Resultados para la placa: {{ placa }}</h2>
            <div align="center">
          <table border="1">
            <tbody>
              <tr>
                <td align="center"><font color="#0A9AD4" size="4">PLACA DE UNIDAD</font></td>
                <td align="center"><font color="#0A9AD4" size="4">VIGENCIA DESDE</font></td>
                <td align="center"><font color="#0A9AD4" size="4">VIGENCIA HASTA</font></td>
                <td align="center"><font color="#0A9AD4" size="4">ESTADO</font></td>
                <td align="center"><font color="#0A9AD4" size="4">Gestion Permiso</font></td>
              </tr>
              <tr>
                <td align="center"><font color="#0B9244">BVR368</font></td>
                <td align="center"><font color="#0B9244">2023-11-27</font></td>
                <td align="center"><font color="#0B9244">2024-11-27</font></td>
                <td align="center"><font color="#0B9244">VIGENTE</font></td>
                <td align="center">
                  <font color="#0B9244"><a href="gestion_permiso.php?valor=103045">Gestionar</a></font>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
    </div>
  </div>
  <div class="wrapper">
    <nav>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/about">About</RouterLink>
    </nav>
  </div>
  <RouterView />
</template>

<script>
export default {
  data() {
    return {
      placa: '',
      submitted: false,
      results: null,
    };
  },
  methods: {
    submitForm() {
      this.submitted = true;
      fetch('https://intranet.afocatregioncentro.pe:843/SistemaPrimeAfocat.WService/afiliacion/getplaca/' + this.placa)
        .then(response => response.json())
        .then(data => {
          this.results = data;
        })
        .catch(error => console.error('Error:', error));
    },
  },
};
</script>

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
