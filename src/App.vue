<template>
  <div id="app">
    <div class="container">
      <shorty-logo></shorty-logo>
      <shorty-add></shorty-add>
    </div>
  </div>
</template>

<script>
import ShortyLogo from './components/ShortyLogo.vue'
import ShortyAdd from './components/ShortyAdd.vue'

export default {
  name: 'App',
  components: {
    ShortyLogo,
    ShortyAdd
  }
}
</script>

<style>

  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  html {
    background-color: #F6F6F6;
    color: #525253;
    font-family: 'Lato', sans-serif;
  }

  .container {
    margin: 0 auto;
    max-width: 960px;
  }

</style>



