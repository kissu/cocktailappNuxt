<template>
    <div class="m-5">
  <h2>Welcome to the Drink App!</h2>
<div>
    <br>
    <div>Choose a drink!</div>
    <div>
        <img class="h-3/4 w-3/4 mt-2.5" src="~/assets/drinks.jpg"/>
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

