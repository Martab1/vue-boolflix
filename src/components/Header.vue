<template>
  <header>
      <section class="container flex">
        <!-- LOGO -->
        <div>
            <img src="../assets/logo.png" alt="logo">
        </div>

       <!-- NAV -->
        <nav>
            <ul class="flex">
                <li> Home</li>
                <li> Series TV</li>
                <li> Movies</li>
                <li> Originals</li>
                <li> Recently added</li>
                <li> My list</li>
            </ul>
        </nav>

        <form>
            <!-- SEARCH BAR -->
            <input type="text"
                    placeholder="search movies or tv series"
                    v-model.trim="searching"
                    @keyup=" $emit('key',searching)"
                   
            />
            
            <!-- BUTTON -->
            <button
                type="submit"
                @click.prevent =" $emit('clickButton', searching)" 
                
                >
                <i class="fa fa-search"/>
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
             searching:"",
         }
     },
  
}
</script>



<style scoped lang="scss">
@import "../styles/utilities.scss";
@import "../styles/vars.scss";

header{
    padding: 10px;
    position:fixed;
    top:0;
    left:0;
    right: 0;
    z-index: 2;
     nav {
         position: absolute;
         left: 380px;
     } ul li {
        cursor:pointer;
        color: $nav;
        transition: .4s;
        &:hover{
            color:$text;
        }
    }
}

nav ul li:not(:last-child){
     margin-right: 15px;
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
    background: $bgInput;
    color:$text;
    outline: none;
    border-radius: 3px;
    &:focus{
      border: 1px solid rgb(163, 29, 29);
    }
}  

// btn search

button{
    cursor: pointer;
    height: 30px;
    width: 30px;
    border: none;
    border-radius: 50%;
    text-transform: uppercase;
    background: transparent;
    color: $text;
    font-size: 1rem;
    .fa-search{
        background:transparent;
    }
}






</style>