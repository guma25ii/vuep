<template>
  <div id="app">
    <h1>Hello Vue</h1>

    <p>
      Välkommen
      {{ user.firstName }}
      {{ user.lastName }}
    </p>

    <div>
      Du har klickat {{ clicked }} gånger!!

      <button @click="onClick">
        Klicka
      </button>

      <div v-if="clicked > 5">
        Bra klickat!
      </div>

      <UserForm
        :user="user"
        @save="handleSubmit"
      />

      <Pokemon />

    </div>
  </div>
</template>

<script>
import UserForm from "./components/UserForm.vue";
import Pokemon from "./components/PokemonCard.vue";

export default {
  name:"App",

  components:{
    UserForm,
    Pokemon
  },

  data(){
    return{
      user:{
        firstName: localStorage.getItem("firstName") || "",
        lastName: localStorage.getItem("lastName") || ""
      },

      clicked:0
    }
  },

  methods:{
    onClick(){
      this.clicked++
    },

    handleSubmit(updatedUser){

      this.user = updatedUser

      localStorage.setItem(
        "firstName",
        updatedUser.firstName
      )

      localStorage.setItem(
        "lastName",
        updatedUser.lastName
      )
    }
  }
}
</script>

<style>
#app{
  font-family:Arial;
  text-align:center;
  margin-top:40px;
}
</style>