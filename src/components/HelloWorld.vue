<template>
  <div id="app">
    <div class="contain">
      <h2>Blog Posts</h2>
      <div class="new">
        <h3>Add a New Post</h3>
        <form @submit.prevent="addPost">
          <input type="text" v-model="newTitle" placeholder="title" required>
          <input type="text" v-model="newAuthor" placeholder="author name" required>
        <select name="" id="" v-model="newLabel" required>
          <option disabled value="">Add a new Label</option>
          <option >C</option>
          <option >C++</option>
          <option>Java</option>
          <option >Python</option>
          <option>Perl</option>

        </select>
        <button type="submit">Add a new Blog posts</button>
        </form>
      </div>
      <select  v-model="selected">
        <option disabled value="">Filter with label</option>
        <option >C</option>
          <option >C++</option>
          <option >Java</option>
          <option >Python</option>
          <option >Perl</option>
      </select>
      <div v-for="post in filteredByLabel" :key="post.id"  class="post">
        <span class="label">{{ post.label }}</span>
        <p>{{ post.title }}</p>
        <small>{{ post.author }}</small>
      </div>
    </div>
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
   selected:'',
   posts:[
    {
      author:"Yashwant kanetkar",
      title:'C Language',
      label:"C"
    },
    {
      author:"Dennis Ritchie",
      title:'C Language',
      label:"C"
    },
    {
      author:" Larry Wall ",
      title:'Perl Language',
      label:"perl"
    },

    {
      author:"James Gosling",
      title:'Java',
      label:"Java"
    },
    {
      author:"Orelly ",
      title:'Java',
      label:"Java"
    },
    {
      author:"Guido Vann Rossam",
      title:'Python Language',
      label:"python"
    }
   ],
   newTitle:'',
   newAuthor:'',
   newLabel:'',
  }
 },
 methods:{
  addPost(){
    let addedPost=new Object({
      title:this.newTitle,
      author:this.newAuthor,
      label:this.newLabel
    });
    this.posts.push(addedPost)//added data to posts object
    this.newTitle='',
    this.newAuthor='',
    this.newLabel='';
  }
 },

 computed:{
  filteredByLabel(){
    let filter=new RegExp(this.selected,'i')
    return this.posts.filter(el=>el.label.match(filter))
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
  text-align: center;
  padding: 70px;
  font-size:22px;
  max-width: 360px;
  margin:0 auto;

}

.contain{
  widows: 400px;
  padding: 10px 40px;
}

input,select{
  font-family: 'Times New Roman', Times, serif;
}

.new,.post{
  background:rgb(219, 215, 215);
  border:1px solid black;
  border-radius: 10px;
  padding: 10px 20px;
  margin:5px 0 10px;
 
}
.label{
  border:1px solid black;
  background:blue;
}
</style>
