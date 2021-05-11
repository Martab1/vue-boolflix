<template>
   <div class="box">
       <!-- image -->
       <img class="film-image" :src="`https://image.tmdb.org/t/p/w342/${details.poster_path}`" alt="">
    

      <ul>
          <!-- title -->
        <h3>  <span>Title:</span> 
             {{ details.title == undefined ? details.name : details.title }} </h3>

        <h3> <span>Original Title: </span> 
            {{ details.original_title === undefined ? details.original_name : details.original_title }}</h3>

        <!-- languages -->
         <h3>  <span>Original language:</span> </h3> 
        <li  v-if="details.original_language === 'en'" >
            <img class="flag" src="../assets/en.png" alt=""></li>

        <li v-else-if ="details.original_language === 'it'"> 
             <img class="flag" src="../assets/it.png" alt=""> </li>

        <!--  stars vote -->
        <li>Vote: {{ details.vote_average }}</li>

        <!-- overview -->
        <li class="over">Overview: {{ details.overview }}</li>
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
     z-index: 2;
     position: absolute;
     bottom:0 ;
     left: 1rem;
     transform: translateY(-50%);
     list-style: none;
     color: #fff;
     opacity: 0;
     transition:  0.4s;
    }

ul,li,h3,span{
    background: transparent;
}



.over{
        max-height: 10rem;
        margin-bottom: 1rem;
        overflow: hidden;   
}

.flag{
   width: 30px;
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

</style>