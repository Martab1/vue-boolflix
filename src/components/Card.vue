<template>
   <div class="box">
     <ul>
        <h2>Title: {{ details.title }}</h2>
        <li>Original Title: {{ details.original_title }}</li>
        <li>Original language: {{ details.original_language }}</li>
        <li>Vote: {{ details.vote_average }}</li>
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

<style>

</style>