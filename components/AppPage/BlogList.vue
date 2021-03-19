<template>
   <div>
      <div class="headerright">
         <h2>List Blog</h2>
       <!--  <Table :dataBlogs="dataBlogs" /><!-->
         <Table  />
      </div>
   </div>
</template>
<script>
   import axios from 'axios'
   import Table from './table-blog.vue'
   export default {
     name: 'admin',
     components: {
       Table
     },   
   }  
</script>