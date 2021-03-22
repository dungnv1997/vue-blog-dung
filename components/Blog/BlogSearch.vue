<template>
  <div>
    <h2>Search Blog</h2>
    <div>Tiêu đề <input v-model="search" placeholder="tiêu đề" /></div>
    <button type="button" placeholder="Tiêu đề.." class="btn btn-success" @click="searchBlog()">
      Search
    </button>
  </div>
</template>
<script>
   export default {
     name: "admin",
     data() {
       return {
         search:'',
       }
     },
     methods: {
      searchBlog() {
        this.$emit('button-clicked',this.search);
      }
    }
   };
</script>
