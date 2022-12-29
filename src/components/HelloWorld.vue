<template>
 <div id="app">
     <table border="2" v-bind:cellspacing="5" v-bind:cellpadding="10">
      <thead>
        <tr>
          <th>ID</th>
          <th>Name</th>
          <th>UserName</th>
          <th>Email</th>
          <th>City</th>
          <th>Phone</th>
          <th>Company Name</th>
        </tr>
      </thead>

      <tbody>
          <tr v-for="user in users" :key="user.id">
            <td>{{ user.id }}</td>
            <td>{{ user.name }}</td>
            <td>{{ user.username }}</td>
            <td>{{ user.email }}</td>
            <td>{{ user.address.city }}</td>
            <td>{{ user.phone }}</td>
            <td>{{ user.company.name }}</td>
          </tr>
      </tbody>
     </table>
 </div>
</template>




<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return{
          title:"Fetching the Data from Jsonplaceholders...",
          intro:"Getting the Data from Jsonplaceholders...",
          users:[]
    }
  },

  computed:{

  },

  created(){
    console.log("It will execute when the component is created")
  },
  mounted(){
    this.fetchUsers();
    console.log("It will execute when the component is mounted")
  },

  methods:{
    fetchUsers(){
      fetch("https://jsonplaceholder.typicode.com/users")
      .then((response) =>response.json())
      .then((data)=>{
        //use loop mechanism to get the
        // for(let i=0;i<data.length;i++){
        //   console.log(`Name ${data[i].name}`);
        // }
        this.users=data;

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
  background: rgb(246, 226, 226);
  margin: auto;
  text-align: center;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}


table:hover{
  background-color: greenyellow;
  cursor:pointer
}


</style>
