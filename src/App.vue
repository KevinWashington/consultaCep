<template>
  <Header />
  <CepForm />
</template>

<script>
import CepForm from './components/CepForm.vue';
import Header from './components/Header.vue';
export default {
    name: "App",
    components: { CepForm, Header }
}
</script>

<style>
  *{ 
    box-sizing: border-box;
    padding: 0;
    margin: 0;
    font-family: Helvetica, sans-serif;
  }
  
  #app {
    background: #dde1e7;
    min-height: 100vh;
  }
</style>
