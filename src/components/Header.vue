<template lang="">
   <div class="nav">
      <router-link to="/" href="#">Home</router-link>
      <router-link to="/add" href="#">Add Restaurant</router-link>
      <a href="#" v-on:click="logout">Logout</a>
   </div>
</template>
<script>
export default {
   name:"Header",
   methods:{
      logout(){
         localStorage.clear();
         this.$router.push({name:'Login'})
      }
   }
}
</script>
<style>
   .nav {
   display: flex;
   justify-content: flex-start;
   align-items: center;
   flex-direction: row;
   width: 100%;
   height: 50px;
   overflow: hidden;
   background: #333;
}

.nav a {
   margin: 0 10px;
   text-decoration: none;
   color: #f2f2f2;
   text-align: center;
   height: 100%;
   line-height: 50px;
   padding:0 5px
}
.nav a:hover{
   color: #333;
   background: #ddd;
   
}
</style>