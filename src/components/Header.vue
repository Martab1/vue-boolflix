<template>
  <header>
      <section class="container flex">
        <!-- logo -->
        <div>
            <img src="../assets/logo.png" alt="logo">
        </div>

        <form >
            <!-- search bar -->
            <input type="text"
                    placeholder="search movies or tv series"
                    v-model.trim="searching"
            />
            
            <!-- button -->
            <button
                type="submit"
                @click.prevent =" $emit('clickButton', searching)"
                
                >
                search
            </button>
        </form>
      </section>

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
@import "../styles/utilities.scss";

header{
    background: rgb(23, 23, 24);
}

.container{
    justify-content: space-between;
    align-items: center;
    
}

input{
    width: 300px;
    padding:5px 8px;
    margin-right: 10px;
    border: none;
    background: rgb(36, 35, 35);
    color:#fff;
    outline: none;
}  

</style>