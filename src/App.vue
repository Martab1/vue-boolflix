<template>
     <section>
       <Header @clickButton="getMovies" />  
       <Main :movies ="moviesList" :series="tvSerieList"/>  
     </section>
</template>

<script>
import axios from "axios";
import Header from "@/components/Header.vue";
import Main from "@/components/Main.vue";

export default {
  name: 'App',
  components: {
    Header,
    Main,
    
  },
  data(){
    return{
        moviesList:[], 
        tvSerieList:[],
        moviesAPI: 'https://api.themoviedb.org/3/search/movie',
        tvAPI: 'https://api.themoviedb.org/3/search/tv',
    }
  },
  methods:{
      getMovies(search){
            // API CALL movies
            axios.get(this.moviesAPI, {
                params: {
                api_key: 'a1f0787be082c3c3dbbeea4cb6f5f368',
                query: search,
                language: "en-EN",
                }
            })
            // API CALL tv
            axios.get(this.tvAPI,{
                params: {
                api_key: 'a1f0787be082c3c3dbbeea4cb6f5f368',
                query: search,
                language: "en-EN",
                }
            })
            .then((res)=> {
                //  console.log(res.data.results);
                this.moviesList = res.data.results;    
                this.tvSerieList = res.data.results;
            })
            .catch((err) => {
              console.log("Errore", err);
            });
        },
  }
 
  
}
</script>

<style lang="scss">
@import "./styles/general.scss";

</style>
