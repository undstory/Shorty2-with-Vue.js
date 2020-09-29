<template functional> <!-- komponent funkcyjny -->
  
    <header class="header">
            <h1 class="header__title">Shorty</h1>
    </header>
    
</template>

<script>
export default {
  name: 'shorty-logo',
  // data() {
  //   return {
  //     sitename: 'Shorty'
  //   }
  // }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style  lang="scss">


  .header {

    &__title {
      background-color: #175242;  
      display: inline-block;
      padding: 4rem 1rem 1rem 1rem;
      color: #F6F6F6;
      font-weight: 400;
      font-family: 'Patua One', cursive;
      font-size: 3rem;
    }
    
  }
</style>
