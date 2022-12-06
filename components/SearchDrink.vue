<template>
    <form @submit.prevent="onSubmit">
        <input type="text" v-model="search" 
        placeholder="search a drink..">
        <input class=button type="submit" value="Search a drink" placeholder="search a drink..">
      </form>
</template>

<script>
export default {
    name: 'SearchDrink',
    data(){
        return{
            search: ''
           
        }
    },
    methods: {
        onSubmit(){
      this.$emit('search-text', this.search)
      this.text= ''
    }
    }

}
</script>

<style>

</style>