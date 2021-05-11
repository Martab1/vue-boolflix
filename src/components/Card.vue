<template>
   <div class="box">
       <!-- IMAGE -->
       <img v-if ="details.poster_path" class="film-image" :src="`https://image.tmdb.org/t/p/w342/${details.poster_path}`" alt="">
       <div class="no-poster" v-else> movie poster temporarily unavailable</div>

      <ul>
          <!-- TITLE -->
        <h3 class="title weight">  <span class="info weight">Title:</span> 
             {{ details.title == undefined ? details.name : details.title }} </h3>

        <h3 class="title weight"> <span class="info weight">Original Title: </span> 
            {{ details.original_title === undefined ? details.original_name : details.original_title }}</h3>

        <!-- LANGUAGES -->
         <h3>  <span class="info weight">Original language:</span> </h3> 
         
         <li  v-if="details.original_language === 'en'" >
            <img class="flag" src="../assets/en.png" alt=""></li>

        <li v-else-if ="details.original_language === 'it'"> 
             <img class="flag" src="../assets/it.png" alt=""> </li>

        <!--  STARS VOTE -->
        <li class="weight" >Vote: {{ details.vote_average }}</li>

        <!-- OVERVIEW -->
        <li class="weight"> Overview: {{ details.overview }}</li>
    </ul>

   </div>
</template>

<script>
export default {
    name: "Card",
    // props card >> main
     props: ["details"],
 
     
}
</script>

<style scoped lang="scss">
@import "../styles/utilities.scss";



// BOX
.box{
    cursor: pointer;
    position: relative;
    width: 340px;
    height: 500px;
    margin-bottom: 40px;
    overflow: hidden; 
    &:hover{
        ul{
            opacity: 1;
        }
    }
}

.film-image{
     position: absolute;
     top: 0;
     left: 0;
     object-fit: contain;   
  }


ul {
     z-index: 1;
     position: absolute;
     bottom:0 ;
     left: 20px;
     transform: translateY(-50%,-50%);
     color: #fff;
     opacity: 0;
     transition: opacity .7s;
    }

ul,li,h3{

    padding: 2px 0;
    background: transparent;
}


.flag{
   width: 30px;
   padding: 5px 0;
}



//  OVERLAY 

.box::after{
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    height: 100%;
    width: 100%;
    background-color: rgba(rgb(24, 23, 23), 0.8);
    opacity: 0;
    transition: opacity 0.4s;
}

.box:hover::after,
.box:hover{
    opacity:1;
}

// controllo film senza poster
.no-poster{
   margin-top: 200px;
   text-transform: uppercase;
   text-align: center;
   font-size: 20px;
   
}

</style>