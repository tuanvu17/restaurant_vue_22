<template lang="">
   <Header />
   <h1>Hello User, Welcome on Add Restaurant Page</h1>
   <div class="add" >
      <input type="text" name="name" placeholder="Enter Name" v-model="restaurant.name">
      <input type="text" name="address" placeholder="Enter Address" v-model="restaurant.address">
      <input type="text" name="contact" placeholder="Enter Contact" v-model="restaurant.contact">
      <button v-on:click="addRestaurant">Add new Restaurant</button>
   </div>
 </template>
<script>
import Header from './Header.vue';
import axios from 'axios';
export default {
   name: 'Add',
   components: {
      Header
   },
   data() {
      return {
         restaurant: {
            name: '',
            address: '',
            contact: ''
         }
      }
   },
   methods: {
      async addRestaurant() {

         const result = await axios.post("http://localhost:3000/restaurant", {
            name: this.restaurant.name,
            contact: this.restaurant.contact,
            address:this.restaurant.address
         }
         )
         if(result.status == 201){
            this.$router.push({ name: 'Home' });
         }else{
            alert('Add Restaurant Failed')
         }
      }
   },
   mounted() {
      let user = localStorage.getItem('user-info');
      if (!user) {
         this.$router.push({ name: 'SignUp' });
      }
   }
}
</script>
<style scoped>

</style>