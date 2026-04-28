<template>
<form @submit="handleSubmit">

  Förnamn:
  <input
    type="text"
    v-model="formUser.firstName"
  />
  <br>

  Efternamn:
  <input
    type="text"
    v-model="formUser.lastName"
  />
  <br>

  <button>Spara</button>

</form>
</template>

<script>
export default{
 name:"UserForm",

 props:{
   user:Object
 },

 data(){
   return{
     formUser:{
       firstName:this.user.firstName || "",
       lastName:this.user.lastName || ""
     }
   }
 },

 methods:{
   handleSubmit(e){
     e.preventDefault()

     this.$emit(
       "save",
       this.formUser
     )
   }
 }
}
</script>