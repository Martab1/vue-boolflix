<template>
   <main class="container">
      <Card v-for="movie in moviesList" :key="movie.id" :details="movie" />
      

   </main>
</template>

<script>
// importo axios 
import axios from "axios";
//importo figlio card
import Card from "@/components/Card.vue"

export default {
    name: "Main",
    components:{
        Card,
    },
    data(){
        return{
           moviesList:[], 
           moviesAPI: 'https://api.themoviedb.org/3/search/movie',

        };
    },
    // created(){
    //     this.getMovies()
    // },
    methods: {
        getMovies(){
            // API CALL 
            axios.get(this.moviesAPI, {
                params: {
                api_key: 'a1f0787be082c3c3dbbeea4cb6f5f368',
                query: "fantozzi",
                language: "en-EN"
                }
            })
            .then(res => {
                //  console.log(res.data.results);
                this.moviesList = res.data.results;     
             
            })
            .catch(err => {
              console.log("Errore", err);
            });
        },
        
        
    },
   

}
</script>

<style scoped lang="scss">


</style>