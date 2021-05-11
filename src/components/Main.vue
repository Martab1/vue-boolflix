<template>
   <main class="container flex">
       <!-- movie card -->
      <Card v-for="movie in movies" :key="movie.id" :details="movie"/>
      <!-- series card -->
      <Card v-for="serie in series" :key="serie.id" :details="serie"/>
     
   </main>
</template>

<script>
//importo figlio card
import Card from "@/components/Card.vue"

export default {
    name: "Main",
    components:{
        Card,
    },
    // props main >> app 
    props:["movies" , "series"],  
   
}
</script>


<style scoped lang="scss">
@import "../styles/utilities.scss";

.container{
    padding: 30px;
    flex-wrap: wrap;
   
}


</style>