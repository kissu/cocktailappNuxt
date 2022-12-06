<template>
<div class="drink">
    <p> {{ drink }}</p>
</div>

</template>

<script>
export default {
    name: 'Drink',
    props: ['drink', 'id']
}
</script>

<style>
 .drink{
    padding: 1rem; 
    border: 1px dotted #ccc;
    margin: 1rem 0; 
 }
</style>