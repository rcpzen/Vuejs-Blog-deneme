<template>
  <div v-theme:column="'narrow'" id="show-blogs">
      <h1>All Blog Articles</h1>
      <input type="text" v-model="search" placeholder="search blogs" />
      <div v-for="(blog,index) in filteredBlogs" :key="index" class="single-blog">
          <h3 v-rainbow>{{blog.title | to-uppercase}}</h3>
          <article>{{blog.body | snippet}}</article>
      </div>
  </div>
</template>

<script>


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
      this.$http.get('https://jsonplaceholder.typicode.com/posts')
      .then(data=>{
          this.blogs=data.body.slice(0,10);
      })
  },
  computed:{
      filteredBlogs:function(){
          return this.blogs.filter(blog=>{
              return blog.title.match(this.search);
          })
      }
  }
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
