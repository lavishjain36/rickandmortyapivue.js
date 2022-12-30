<template>
<div id="app">
  <h1>Brewery List of Items</h1>
  <table border="2" cellspacing="5" cellpadding="5">
      <thead>
        <tr>
          <th>Name</th>
          <th>Brwery Type</th>
          <th>City</th>
          <th>State</th>
          <th>Country</th>
          <th>Postal Code</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="brewery in breweries" :key="brewery.id">
           <td>{{ brewery.name }}</td>
           <td>{{ brewery.brewery_type }}</td>
           <td>{{ brewery.city }}</td>
           <td>{{ brewery.state }}</td>
           <td>{{ brewery.country }}</td>
           <td>{{ brewery.postal_code }}</td>
        </tr>
      </tbody>
  </table>
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
      breweries:[]
    }
  },
  mounted(){
    axios.get("https://api.openbrewerydb.org/breweries")
    .then(response=>{
    
      this.breweries=response.data;
     
    })
    .catch(error=>{
      console.log(error)
    })
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
  margin-left:200px;
}

table:hover{
  background-color: greenyellow;
  cursor:pointer
}


</style>
