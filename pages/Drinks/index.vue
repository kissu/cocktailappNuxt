<template>
  <div>
  <div>
    <form>
      <input type="text" v-model="search" 
      placeholder="search a drink..">
    </form>
  </div>
  <div>
  <div v-for="drink in drinks" :key="drink.idDrink"> 
  <nuxt-link :to="`/drinks/${drink.idDrink}`">
    <div class="drink">
    <p> {{ drink.strDrink }} </p>
    <img :src="drink.strDrinkThumb" alt=""/> 
    <p>Instructions:</p>
    <p> {{ drink.strInstructions }} </p>
    <div class="ing"> Ingridients: 
      <ul>
        <li>{{ drink.strIngredient1 }} </li>
        <li>{{ drink.strIngredient2 }} </li>
        <li>{{ drink.strIngredient3 }} </li>
        <li>{{ drink.strIngredient4 }} </li>
        <li>{{ drink.strIngredient5 }} </li>
      </ul>
  </div>
  </div>
</nuxt-link>
</div>
</div>
</div>
</template>

<script>
import axios from 'axios'

export default {
  data(){
    return {
      drinks: [],
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
 computed:{
    searchDrink(){
      if(this.search === null){
        return this.drinks.drink
      }else{
        return this.drinks.filter(drink => drink === this.drinks)
    
    }
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
.drink{
  padding: 1rem; 
  border: 1px dotted #ccc;
  margin: 1rem 0;
}
img{
  height: 250px;
  width: 250px; 
}

</style>