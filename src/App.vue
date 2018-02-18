<template>
  <div>
    <show-blog></show-blog>
  </div>
</template>

<script>
import addBlog from './components/addblog.vue';
import showBlogs from './components/showBlogs.vue';

export default {
  components:{
    'add-blog':addBlog,
    'show-blog':showBlogs
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
