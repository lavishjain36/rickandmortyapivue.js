<template>
<div id="app">
   <div id="test" v-for="data of info" v-bind:key="data.id">
    {{ data.name }} <br>
    {{ data.species }} <br>
    {{ data.gender }} <br> 
    <img v-bind:src="data.image">
   
   </div>
  <button @click="fetch">Submit</button>
</div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return{
      info:[]
    }
  },
  methods:{
  fetch(){
    axios.get("https://rickandmortyapi.com/api/character")
    .then(res=>{
      // console.log(res.data.results);
      this.info=res.data.results;
      
    })
  }  
  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

#app{
  margin-left:0;
}

#test{
  background-color: rgb(255, 198, 42);
  width: 600px;
}

img{
  border:2px solid red;
  border-radius: 50%;
}

</style>
