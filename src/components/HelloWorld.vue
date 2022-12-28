<template>
    <div id="app">
      <img v-bind:src="picture"
      :alt="`${firstName} ${lastName}`"
      :class="gender"
      />
      <h1>{{ firstName }} {{ lastName }}</h1>
      <h3>Email:{{ email }}</h3>
      <h4>Gender:{{ gender }}</h4>
      <button :class="gender" @click="getUser()">Get a Random User</button>


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
      firstName:"John",
      lastName:"Doe",
      email:"john@gmail.com",
      gender:"male",
      picture:"https://randomuser.me/api/portraits/men/60.jpg"
    }
  },
  methods:{
    async getUser(){
      const res=await fetch("https://randomuser.me/api/")
      const {results}=await res.json()
      // console.log(results)

      this.firstName=results[0].name.first;
      this.lastName=results[0].name.last;
      this.email=results[0].email;
      this.gender=results[0].gender;
      this.picture=results[0].picture.large;
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
  background-color: rgb(246, 226, 226);
  width:400px;
  height: 100vh;
  margin: auto;
  text-align: center;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}


h1,h3{
  margin-bottom: 8px;
  font-weight: normal;
}

img{
  border-radius: 50%;
  border:5px solid rgb(255, 0, 191);
  margin-bottom: 8px;
}


.male{
  border-color:aquamarine;
  background-color:rgb(171, 115, 245) ;
}

.female{
  border-color:rgb(219, 64, 175);
  background-color:rgb(245, 245, 115) ;
}

button{
  cursor:pointer;
  display: inline-block;
  background: white;
  color:black;
  font-size: 18px;
  border:0;
  border-radius: 20px;
}

button:hover{
  background-color: yellow;
}
</style>
