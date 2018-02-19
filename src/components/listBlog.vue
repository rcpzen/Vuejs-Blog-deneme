<template>
  <div v-theme:column="'narrow'" id="show-blogs">
      <h1>List Blogs Titles</h1>
      <input type="text" v-model="search" placeholder="search blogs" />
      <div v-for="(blog,index) in filteredBlogs" :key="index" class="single-blog">
          <h3 v-rainbow>{{blog.title | to-uppercase}}</h3>
          
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
      this.$http.get('https://jsonplaceholder.typicode.com/posts')
      .then(data=>{
          this.blogs=data.body.slice(0,10);
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
