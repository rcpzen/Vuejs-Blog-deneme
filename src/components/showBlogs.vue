<template>
  <div id="show-blogs">
      <h1>All Blog Articles</h1>
      <input type="text" v-model="search" placeholder="search blogs" />
      <div v-for="(blog,index) in filteredBlogs" :key="index" class="single-blog">
          <router-link :to="'/blog/'+ blog.id"><h3>{{blog.title | to-uppercase}}</h3></router-link>
          <article>{{blog.content | snippet}}</article>
      </div>
  </div>
</template>

<script>
import searchMixin from '../mixins/searchMixin';

export default {

  name: 'app',
  data () {
    return {
        blogs:[],
        search:''
    }
  },
  methods:{

  },
  created(){
      this.$http.get('https://vueblog-5e9d6.firebaseio.com/posts.json')
      .then(function(data){return data.json();})
      .then(function(data){
          var blogsArray=[];
          for (let key in data) {
             data[key].id=key;
             blogsArray.push(data[key]);
             console.log(data[key]);
              
          }
          this.blogs=blogsArray;
           console.log(blogsArray);
           })
  },
  computed:{
     
  },
   mixins:[searchMixin]
}
</script>

<style>
input[type="text"]{
    border: 1px solid #eee;
    padding: 8px;
    margin: 5px 0;
    width: 100%;
}
#show-blogs{
    max-width: 800px;
    margin:0 auto;
}

.single-blog{
    padding: 20px;
    margin: 20px 0;
    box-sizing: border-box;
    background: #eee;
}



</style>
