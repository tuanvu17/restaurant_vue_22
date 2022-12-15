<template>
   <div>
      <router-view />
   </div>
</template>

<script>

export default {
   name: 'App',
}
</script>

<style>
#app {
   font-family: Avenir, Helvetica, Arial, sans-serif;
   -webkit-font-smoothing: antialiased;
   -moz-osx-font-smoothing: grayscale;
   text-align: center;
   color: #2c3e50;
   /* margin-top: 60px; */
}


.logo {
   width: 100px;
}

.register,
.login, 
.add,
.home {
   display: flex;
   justify-content: center;
   align-items: center;
   flex-direction: column;
}

.register input,
.login input,
.add input {
   height: 30px;
   width: 300px;
   border: 1px solid;
   padding: 5px;
   border-radius: 10px;
   display: block;
   margin: 10px;
   outline: none;
}

.register button,
.login button,
.add button {
   height: 35px;
   width: 300px;
   border-radius: 10px;
   outline: none;
   border: none;
   cursor: pointer;
   transition: all .5s ease;
   font-size: 16px;
   margin-top: 20px;
}

.register button:hover,
.login button:hover,
.add button:hover {
   background-color: gray;
   color: white;
}
</style>
