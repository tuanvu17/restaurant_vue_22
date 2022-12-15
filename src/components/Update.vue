<template lang="">
   <Header />
   <h1>Hello User, Welcome on Update Restaurant Page</h1>
   <div class="add" >
      <input type="text" name="name" placeholder="Enter Name" v-model="restaurant.name">
      <input type="text" name="address" placeholder="Enter Address" v-model="restaurant.address">
      <input type="text" name="contact" placeholder="Enter Contact" v-model="restaurant.contact">
      <button v-on:click="updateRestaurant">Update Restaurant</button>
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
      async updateRestaurant() {
         console.log("result: ", this.restaurant);
         const result = await axios.put("http://localhost:3000/restaurant/"+this.$route.params.id, {
            name: this.restaurant.name,
            contact: this.restaurant.contact,
            address:this.restaurant.address
         }
         )
         if(result.status == 200){
            this.$router.push({ name: 'Home' });
         }else{
            alert('Add Restaurant Failed')
         }
      }
   },
   async mounted() {
      let user = localStorage.getItem('user-info');
      if (!user) {
         this.$router.push({ name: 'SignUp' });s
      }
      const result = await axios.get("http://localhost:3000/restaurant/"+this.$route.params.id);
      this.restaurant = result.data
   }
}
</script>
<style scoped>

</style>