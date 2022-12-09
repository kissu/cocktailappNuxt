<template>
  <div class="about">
    <h1>About Drinks</h1>
    <br>
    <p>This is an app that displays different drinks.</p>
    <br>
    <p>A drink or beverage is a liquid intended for human 
        consumption. In addition to their basic function 
        of satisfying thirst, drinks play important roles 
        in human culture. Common types of drinks include 
        plain drinking water, milk, juice, smoothies and 
        soft drinks. Traditionally warm beverages include 
        coffee, tea, and hot chocolate. Caffeinated drinks 
        that contain the stimulant caffeine have a long history.</p>
  </div>
</template>

<script>
export default {
    head(){
        return {
            title: 'About The App',
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
.about{
    margin: 20px; 
    margin-bottom: 50px; 
}
</style>