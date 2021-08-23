<template>
  <div id="app">
    <Calculadora/>
  </div>
</template>

<script>
  import Calculadora from "./main/Calculadora"

  export default {
    components: { Calculadora }
  }
</script>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  body {
    font-family: sans-serif;
    background-color: black;
    color: white;
  }

  #app {
    display: flex;
    flex-direction: column;
    height: 100vh;
    justify-content: center;
    align-items: center;
    text-align: center;
  }
</style>