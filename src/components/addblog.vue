<template>
  <div id="add-blog">
    <form v-if="!submitted">
        <label>Blog Title</label>
        <input type="text" v-model.lazy="blog.title" required/>
        <label>Blog Content</label>
        <textarea v-model.lazy="blog.content"></textarea>
        <div id="check-box">
          <label>kategori1</label>
          <input type="checkbox" value="kategori1" v-model="blog.categories"/>
          <label>kategori2</label>
          <input type="checkbox" value="kategori2" v-model="blog.categories"/>
          <label>kategori3</label>
          <input type="checkbox" value="kategori3" v-model="blog.categories"/> 
        </div>
        <button v-on:click.prevent="post">Add Blog</button>
    </form>
    <div v-if="submitted">
      <h3>Postunuz gönderildi</h3>
    </div>
    <div id="preview">
        <h3>Preview Blog</h3>
        <p>Blog title:{{blog.title}}</p>
        <p>Blog Content</p>
        <p>{{blog.content}}</p>
        <p>Blog Categories </p>
        <ul>
          <li v-for="(category,index) in blog.categories" v-bind:key="index">{{category}}</li>
        </ul>
    </div>
   
  </div>
</template>

<script>
export default {
  name: 'addblog',
  data () {
    return {
        blog:{
            title:'',
            content:'',
            categories:[]
        },
        submitted:false,
    }
  },
  methods:{
    post:function(){
      this.$http.post('https://jsonplaceholder.typicode.com/posts',{
        title:this.blog.title,
        body:this.blog.content,
        userId:1
      }).then(data=>{
        console.log(data);
        this.submitted=true;
      });
    }
  }
}
</script>


