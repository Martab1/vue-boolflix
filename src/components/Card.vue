<template>
  
   <div class="box relative">
       <!-- IMAGE -->
       <img v-if ="details.poster_path" class="film-image" :src="`https://image.tmdb.org/t/p/w342/${details.poster_path}`" alt="">
       <img  class="width100" v-else src="../assets/poster-placeholder.png" alt="">

      <ul>
          <!-- TITLE -->
        <h4 class="title weight">  <span class="info weight">Title:</span>
             {{ details.title == undefined ? details.name : details.title }} </h4>
         <h4 class="title weight"> <span class="info weight">Original Title: </span> 
            {{ details.original_title === undefined ? details.original_name : details.original_title }}</h4>

        <!-- LANGUAGES -->
        <li class="languages">
            <span class="info weight">Original language:</span> 
            <img v-if="details.original_language === 'en'" class="flag" src="../assets/en.png" alt="">
            <img v-else-if ="details.original_language === 'it'" class="flag" src="../assets/it.png" alt="">
         </li>

        <!--  STARS VOTE -->
        <li class="weight" > Vote: 
            <!-- full star -->
            <i class=" fas fa-star"
                v-for =" star in starsVote(details.vote_average)"
                :key="`full-${star}`"
            ></i>

             <!-- empty star -->
             <i class=" far fa-star"
                v-for =" star in (5 - starsVote(details.vote_average))"
                :key="`empty-${star}`"
             ></i>
         </li>

        <!-- OVERVIEW -->
        <li class="weight overview"> Overview: {{ details.overview }}</li>

      </ul>

   </div>
</template>

<script>
export default {
    name: "Card",
    // props card >> main
     props: ["details"],
     methods:{
         starsVote(vote){
             return Math.ceil( vote / 2);
         }
     }
 
     
}
</script>

<style scoped lang="scss">
@import "../styles/utilities.scss";
@import "../styles/vars.scss";



// BOX
.box{
    cursor: pointer;
    width: 340px;
    height: 500px;
    margin: 0 10px;
    margin-bottom: 40px;
    overflow: hidden; 
    transition: .4s;
    box-shadow: 2px -4px 10px rgb(8, 8, 8);
    &:hover{
        transform: scale(1.1);
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
     bottom:1rem;
     left: 20px;
     transform: translateY(-50%,-50%);
     color: $text;
     opacity: 0;
     transition: opacity .7s;
     font-size: 13px;
     
    }

ul,li,h4{

    padding: 2px 0;
    background: transparent;
}

li{
    padding: 2px 0;
}

.flag{
   width: 30px;
   margin: 5px 5px;
   vertical-align: middle;
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

.overview{
    max-height: 160px;
    overflow: scroll;
    text-align: left;
}

.fas.fa-star,
.far.fa-star{
    color: $star;
    font-size: 14px;
    background: transparent;
}

</style>