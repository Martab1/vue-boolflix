<template>
   <main>
       
       <section >
          
           <!-- movie title -->
           <h2  v-show=" movies.length > 0" 
                class="container movie-title"> 
                boolflix original movies 
            </h2>

           <div class="container movie">
                <!-- movie card -->
                <div class="flex ">
                        <div class="flex "> 
                            <Card v-for="movie in movies" 
                                :key="movie.id" 
                                :details="movie"/>
                        </div>
                </div>
            </div>

        <!-- tv title -->
         <h2 v-show=" series.length > 0 " 
             class="container "> 
             boolflix original series
        </h2>

         <div class="container tv">
                <!-- series card -->
                <div class="flex ">
                        <div class="flex"> 
                            <Card v-for="serie in series" 
                                :key="serie.id" 
                                :details="serie"/>
                        </div>
                </div>
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
@import "../styles/vars.scss";


.container{ 
    padding-top:50px;
    overflow-x: auto;
    
}

.container.movie{
    padding-top: 200px;
}


.movie-title{
    position: relative;
    top: 160px;
}

h2{  
    padding-bottom: 5px;
    text-transform: uppercase;
    color: $h2;  
    border-bottom: 1px solid rgb(201, 72, 72);
}


</style>