<template>
  <header>
      <div>
          logo
      </div>

      <form>
         <input type="text"
                placeholder="search movies"
                v-model.trim="searching"
         />

         <button
          type="submit"
          @click.prevent =" $emit('clickButton', searching)"
         >
          search
         </button>
      </form>
  </header>
</template>

<script>
export default {
     name: "Header",
     data(){
         return{
             searching: "",
         }
     }
}
</script>




<style scoped lang="scss">

</style>