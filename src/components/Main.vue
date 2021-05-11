<template>
   <main>
       <section class="container">

            <!-- movie card -->
            <h2> movies </h2>
            <div class="flex wrap space-around"> 
                <Card v-for="movie in movies" :key="movie.id" :details="movie"/>
            </div>
            
            <!-- series card -->
            <h2> series</h2>
            <div class="flex wrap space-around"> 
                <Card v-for="serie in series" :key="serie.id" :details="serie"/>
            </div>
      
    </section>
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
    padding: 50px ; 
    // background: #fff; 
   
    
}

h2{
    text-transform: uppercase;
    color:rgb(133, 128, 128);
    margin-bottom: 10px ;
}


</style>