<template>
  <div class="home">
    <h1>WELCOME TO VUE JS</h1>
    <div class="cta">
    <router-link to="/register" style="text-decoration:none">Sign Up</router-link>
    </div>
  </div>
</template>

<script>



export default {
  name: 'Home',
  
}
</script>
<style scoped>
.home{
  width: 80%;
    margin: auto;
 
}


  h1 {
    text-align: center;
  }

  p {
    text-align: center;
  }

  .cta {
    width: 300px;
    margin: auto;
    text-align: center;
  }

  .cta a {
    margin: 10px;
    text-decoration: none;
    display: inline-block;
    border: 1px solid #521751;
    border-radius: 3px;
    width: 100px;
    padding: 10px;
    box-sizing: border-box;
    color: #521751;
  }

  .cta a:hover,
  .cta a:active {
    background-color: #521751;
    color: white;
  }

</style>
