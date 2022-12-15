<template lang="">
   <div>
      <img class="logo" src="../assets/logo.png" alt="">
      <h1>Sign Up</h1>
      <div class="register">
         <input type="text" v-model="name" placeholder="Enter Name">
         <input type="text" v-model="email" placeholder="Enter Email">
         <input type="password" v-model="password" placeholder="Enter Password">
         <button v-on:click="signUp">Sign Up</button>
         <p>
            <router-link to="/login">Login</router-link>
         </p>
      </div>
   </div>
</template>
<script>
import axios from 'axios'
export default {
   name: 'SignUp',
   data() {
      return {
         name: '',
         email: '',
         password: ''
      }
   },
   methods: {
      async signUp() {
         const result = await axios.post("http://localhost:3000/users", {
            "name": this.name,
            "email": this.email,
            "password": this.password
         })
         if(result.status == 201){
            // alert("Sign Up OK");
            localStorage.setItem("user-info", JSON.stringify(result.data));
            this.$router.push({name:'Home'})
         }else{
            alert("Sign Up FAILE");

         }
      }
   },
   mounted(){
      // let user = localStorage.getItem('user-info');
      // if(user){
      //    this.$router.push({name:'Home'});
      // }
   }
}
</script>
<style>

</style>