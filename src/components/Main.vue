<template>
   <main class="container">
      <Card v-for="movie in movies" :key="movie.id" :details="movie"/>
     
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
    props:["movies"],  
   
}
</script>


<style scoped lang="scss">
@import "../styles/utilities.scss";
.container{
    padding: 30px;
}


</style>