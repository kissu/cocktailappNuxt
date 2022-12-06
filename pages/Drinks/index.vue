<template>
  <div>
  <div>
    <SearchDrink/>
  </div>
  <div>
  <Drink v-for="drink in drinks" :key="drink.id" 
  :id="drink.id" :drink="drink.drink"/>
</div>
</div>
</template>

<script>
import Drink from '../../components/Drink.vue'
import SearchDrink from '../../components/SearchDrink.vue'
import axios from 'axios'

export default {
  components:{
    Drink,
    SearchDrink,
  },
  data(){
    return {
      drinks: [],
      search: ''
    }
  },
  async created(){
    const config = {
      headers: {
        Accept: 'application/json'
      }
    }
    try{
      const res = await axios.get('www.thecocktaildb.com/api/json/v1/1/random.php',
      config)
      console.log(res.data)
      this.drinks = res.data
    } catch(err){
      console.log(err)
    }
  },

  // methods: {
  //   searchDrink(){
  //     if(!this.search){
  //       return this.drinks
  //     }else{
  //       return this.drinks.filter(drink => 
  //       drink.text.toLowerCase().includes(this.search.
  //       toLowerCase()))
  //     }
  //   }
  // },
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

</style>