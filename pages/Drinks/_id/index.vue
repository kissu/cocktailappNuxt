<template>
  <div>
    <nuxt-link to="/drinks"> Go Back </nuxt-link>
    <div>
    <img :src="drink.strDrinkThumb" alt=""/> 
      <h2>{{ drink.strDrink }}</h2>
      <div class="ing"> <strong>Ingridients: </strong> 
        <ul class="ingrid">
          <li>{{ drink.strIngredient1 }} </li>
          <li>{{ drink.strIngredient2 }} </li>
          <li>{{ drink.strIngredient3 }} </li>
          <li>{{ drink.strIngredient4 }} </li>
          <li>{{ drink.strIngredient5 }} </li>
        </ul>
    </div>
    <p><strong> Instructions: </strong></p>
    <p class="instru"> {{ drink.strInstructions }} </p>
    
    </div>
    <hr />
    <small>Drink ID: {{ $route.params.id }}</small>
  </div>
</template>

<script>
import axios from 'axios'

export default {
    data(){
        return{
            drink: {},
            
        }
    },

    methods: {
    getDrinkById(){
        axios.get(`https://www.thecocktaildb.com/api/json/v1/1/lookup.php?i=${this.$route.params.id}`)
.then((response) => {
	this.drink = response.data.drinks[0]
	console.log(response.data)
})
.catch((error) => {
	console.log(error)
})

}
    },
  created(){
    this.getDrinkById()

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
.ing{
    margin-top: 10px; 
}
.ingrid{
    max-width: 500px; 
    list-style: disc;
    display: flex; 
    flex-direction: column; 
    flex-wrap: wrap; 
    justify-content: space-between; 
    padding: 10px 0px 30px 20px; 
}
.instru{
    padding: 10px 0px 20px;
}
</style>
