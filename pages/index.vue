<template>
    <div class="welcome">
  <h2>Welcome to the Drink App!</h2>
<div>
    <br>
    <div>Choose a drink!</div>
    <div>
        <img class="welcome-img" src="~/assets/drinks.jpg"/>
    </div>
</div>
</div>
</template>

<script>
export default {
    head(){
        return {
            title: 'Welcome to the drinks app',
            meta: [
                {
                    hid: 'description',
                    name: 'description',
                    content: 'Best place to learn about drinks'
                }
            ]
        }
    }
}
</script>
<style>
.welcome{
    margin: 20px; 
}
.welcome-img{
    height: 500px; 
    width: 700px; 
    margin-top: 10px; 
}
</style>
