<template>
<div>

<h1>Pokemon</h1>

<div
 v-if="pokemon.name"
 style="
 margin-bottom:20px;
 border:1px solid black;
 padding:10px;
 "
>
 Name: {{ pokemon.name }} <br>
 Weight: {{ pokemon.weight }} <br>
 Height: {{ pokemon.height }}
</div>


<div>
<a
 v-for="poke in pokemons"
 :key="poke.name"
 href="#"
 @click.prevent="getPokemon(poke.url)"
>
 {{ poke.name }}
 <br>
</a>
</div>

</div>
</template>

<script>
export default{
 name:"PokemonCard",

 data(){
   return{
     pokemons:[],
     pokemon:{}
   }
 },

 created(){
   console.log("Created")

   fetch(
    "https://pokeapi.co/api/v2/pokemon"
   )
   .then(res=>res.json())
   .then(data=>{
      this.pokemons = data.results
   })
 },

 mounted(){
   console.log("Mounted")
 },

 updated(){
   console.log("Updated")
 },

 methods:{
   getPokemon(url){

     fetch(url)
      .then(res=>res.json())
      .then(data=>{
        this.pokemon = data
      })
   }
 }
}
</script>