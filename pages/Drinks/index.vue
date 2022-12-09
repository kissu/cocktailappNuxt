<template>
  <div>
  <div>
    <form>
      <input type="text" v-model="search" 
      placeholder="search a drink..">
    </form>
  </div>
  <div v-if="searchDrink.length">
  <div v-for="drink in searchDrink" :key="drink.idDrink"> 
  <nuxt-link :to="`/drinks/${drink.idDrink}`">
    <div class="drink-container">
    <h3><strong>{{ drink.strDrink }}</strong></h3>
    <div class="drink">
    <img :src="drink.strDrinkThumb" alt=""/> 
    <ul class="ingr">
      <li>{{ drink.strIngredient1 }} </li>
      <li>{{ drink.strIngredient2 }} </li>
      <li>{{ drink.strIngredient3 }} </li>
    </ul>
  </div>
  </div>
</nuxt-link>
</div>
</div>
<div v-else>No Drinks found</div>
</div>
</template>

<script>
import axios from 'axios'

export default {
  data(){
    return {
      drinks: [],
      search: ''
    }
  },
 methods: {
    async getAllDrinks(){
      try{
      const { data} = await axios.get(
        'https://thecocktaildb.com/api/json/v1/1/search.php?s=')

        this.drinks = data.drinks 
      } catch(error) {
      console.log('error', error)
    }
    
    }, 
    
  },
 
   computed: { 
    // searchDrink: function(){
    //   if(this.search.trim().length === 0){
    //     return this.drinks.filter((drink) => 
    //     drink.strDrink.toLowerCase().includes(
    //       this.search.trim().toLowerCase()))
    //   }else{
    //     return this.drinks
    
    // }
    //  }
    searchDrink: function(){
      return this.drinks.filter((drink) =>{
        return drink.strDrink.toLowerCase().match(this.search)
      })
    }
    },
  created(){
    this.getAllDrinks()
    
  
  },
    head(){
        return {
            title: 'Drinks App',
            meta: [
                {
                    hid: 'description',
                    name: 'description',
                    content: 'Best place to search a Drink'
                }
            ]
        }
    }
  }
</script>

<style>
.btn{
  padding: 10px; 
  border-radius: 5px; 
  border: none; 
  background-color: rgb(246, 148, 113);
  margin: 15px; 
  cursor: pointer; 
}
.button:hover {
  background-color: rgb(242, 181, 159);
}
.drink-container{
  padding: 1rem; 
  border: 1px dotted #ccc;
  margin: 1rem 0;
}
img{
  height: 250px;
  width: 250px; 
  border-radius: 3px; 
}
.drink{
  display: flex; 
  gap: 250px;
}
.ingr{
  list-style:disc; 
}

</style>