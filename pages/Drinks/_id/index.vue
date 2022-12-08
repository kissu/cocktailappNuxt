<template>
  <div>
    <nuxt-link to="/drinks">
        Go Back
    </nuxt-link>
    <div v-for="drink in drinks" :key="drink.idDrink" >
    <h2> {{ drink.strDrink}} </h2>
    <li>{{ drink.strIngredient1 }} </li>
    </div>
    <hr>
    <small>Drink ID: {{ $route.params.id }}</small>
  </div>
</template>

<script>
import axios from 'axios'

export default {
    data(){
        return{
            drink: {},
            drinks: []
        }
    },
    async fetch(){
        await this.getAllDrinks(),
        await this.getDrinks()

    },
    methods: {
    async getAllDrinks(){
        try{ 
        const {data} = await axios.get(`www.thecocktaildb.com/api/json/v1/1/lookup.php?i=${this.$route.params.id}`)

        this.drinks = data.drinks
        console.log(data.drinks)
    } catch(error){
      console.log('error', error)
    }
    
    },
    async getDrinks(){
      try{
      const { data} = await axios.get(
        'https://thecocktaildb.com/api/json/v1/1/search.php?s=')

        this.drinks = data.drinks 
      } catch(error) {
      console.log('error', error)
    }
    
    },  
 },
  created(){
    this.getAllDrinks(),
    this.getDrinks()
  },
  head(){
        return {
            title: this.drinks,
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

</style>