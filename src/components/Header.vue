<script setup>
import { ref } from 'vue';
const Title = ref("ABRAHAM TASK RECORDER")


</script>

<template>
  <div class="header">
    <div>
      <h2>{{ Title }}</h2>

    </div>
   <div>
      <div></div>
      <div></div>
      <div></div>
   </div> 
   
  </div>
</template>

<style scoped>
  .header{
    max-width: 95%;
    width: 100%;
    height: 10vh;
    background-color:  #d9138a;
    display: flex;
    align-items: center;
    margin: auto;
    padding: 0 1rem ;
    justify-content: center;
  }
  h2{
    font-size: 2rem;
    color:  black;
  }

  @media only screen and (max-width: 600px) {
    .header{
    max-width: 90%;
    width: 100%;
    height: 7vh;
    background-color: #7a2048;
    display: flex;
    align-items: center;
    margin: auto;
    padding: 0 1rem ;
    justify-content: center;
  }
  h2{
    font-size: 18px;
    color:  black;
  }
  }

  @media only screen and (min-width: 600px) {
    .header{
    max-width: 89%;
    width: 100%;
    height: 6vh;
    background-color:  #7a2048;
    display: flex;
    align-items: center;
    margin: auto;
    padding: 0 1rem ;
    justify-content: center;
  }
  h2{
    font-size: 2rem;
    color:    black;
  }

  }
  @media only screen and (min-width: 768px) {
    .header{
    max-width: 95%;
    width: 100%;
    height: 6.5vh;
    background-color: #7a2048;
    display: flex;
    align-items: center;
    margin: auto;
    padding: 0 1rem ;
    justify-content: center;
  }
  h2{
    font-size: 2rem;
    color:    black;
  }
    
  }
</style>
