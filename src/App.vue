<template>
  <div>
    <app-header></app-header>
    <router-view></router-view>
    
  </div>
</template>

<script>
import addBlog from './components/addblog.vue';
import showBlogs from './components/showBlogs.vue';
import listBlogs from './components/listBlog.vue';
import Header from './components/header.vue';

export default {
  components:{
    'add-blog':addBlog,
    'show-blog':showBlogs,
    'list-blog':listBlogs,
    'app-header':Header
  },
  name: 'app',
  data () {
    return {
    
    }
  }
}
</script>

<style>

</style>
