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
    <div class="p-0.5 border-2 border-slate-200 border-dotted m-1">
    <h3><strong>{{ drink.strDrink }}</strong></h3>
    <div class="flex gap-64">
    <img class="h-64 w-64 rounded" :src="drink.strDrinkThumb" alt=""/> 
    <ul class="list-disc">
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
