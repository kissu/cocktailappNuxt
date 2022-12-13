<template>
  <div>
    <nuxt-link to="/drinks"> Go Back </nuxt-link>
    <div>
    <img class="h-64 w-64 rounded" :src="drink.strDrinkThumb" alt=""/> 
      <h2 class="mt-2"><strong>{{ drink.strDrink }}</strong></h2>
      <div class="mt-2.5"> <strong>Ingridients: </strong> 
        <ul class="max-w-lg list-disc flex flex-col flex-wrap justify-between pt-2.5 pr-0 pb-7 pl-5 ">
          <li>{{ drink.strIngredient1 }} </li>
          <li>{{ drink.strIngredient2 }} </li>
          <li>{{ drink.strIngredient3 }} </li>
          <li>{{ drink.strIngredient4 }} </li>
          <li>{{ drink.strIngredient5 }} </li>
        </ul>
    </div>
    <p><strong> Instructions: </strong></p>
    <p class="pt-2.5 pb-5 "> {{ drink.strInstructions }} </p>
    
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

