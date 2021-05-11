<template>
   <div class="box">
       <!-- image -->
       
    

         <!-- title -->
        <h3> <strong> Title:</strong>
             {{ details.title == undefined ? details.name : details.title }} </h3>

        <h3> <strong>Original Title:</strong> 
            {{ details.original_title === undefined ? details.original_name : details.original_title }}</h3>

      <ul>
        <!-- languages -->
        <strong>  Original language:</strong>
        <li v-if="details.original_language === 'en'" >
            <img src="../assets/en.png" alt=""></li>

        <li v-else-if ="details.original_language === 'it'"> 
             <img src="../assets/it.png" alt=""> </li>

        <!--  stars vote -->
        <li>Vote: {{ details.vote_average }}</li>

        <!-- overview -->
        <li>Overview: {{ details.overview }}</li>
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

.box{
   width: 300px;
   height: 300px;
   overflow: scroll;
   border: 1px solid black;
   margin: 5px 5px;
}

img{
   width: 30px;
}

ul{
    list-style: none;
}

</style>