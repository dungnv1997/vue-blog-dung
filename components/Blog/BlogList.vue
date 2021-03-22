<template>
  <div class="headerright">
    <h3>List Blogs</h3>
    <table class="table table-bordered">
      <thead>
        <tr>
          <th scope="col">ID</th>
          <th scope="col">Tin</th>
          <th scope="col">Loại</th>
          <th scope="col">Trạng thái</th>
          <th scope="col">Vị trí</th>
          <th scope="col">Ngày public</th>
          <th>Edit</th>
          <th scope="col">Delete</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(blog, index) in dataBlogs" :key="index">
          <th scope="row">{{ blog.id }}</th>
          <td>{{ blog.title }}</td>
          <td>{{ filterCategory(blog.category) }}</td>
          <td>{{ blog.public == true ? "Public" : "Private" }}</td>
          <td>{{ filterPosition(blog.position) }}</td>
          <td>{{ blog.data_pubblic }}</td>
          <td>
            <nuxt-link :to="`/blog/${blog.id}`" ><button class="btn btn-primary">Edit</button></nuxt-link>
          </td>
          <td>
            <button class="btn btn-danger" @click="deleteBlog(blog.id)">
              Delete
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
   import axios from 'axios'
   import {
      DATA_CATE,
      DATA_POS
   } from '@/content/content.js'
   export default {
      name: 'ListBlog',
      props: {
         dataBlogs: {
            type: Array,
            default: () => [],
         },
      },
      data() {
         return {
            CATEGORY: DATA_CATE,
            POSITION: DATA_POS,
         }
      },
      methods: {
         /**
          * delete blog
          */
         deleteBlog(id) {
            if(confirm('are you sure?'))
               axios.delete('http://localhost:4000/blogs/' + id).then((res) => {
                  this.$emit('getListBlogs', this.dataBlogs)
               })
                  .catch(error => {
                  console.log(error);
               })
         },
         /**
          * get name position
          */
         filterPosition(pos) {
            return pos
               .map((item) => {
                  return this.POSITION[item]
               })
               .join(',')
         },
         /**
          * get name category
          */
         filterCategory(id) {
            return this.CATEGORY.find((cate, index) => {
               if (index === id) {
                  return cate
               }
            })
         },
      },
   }
</script>
<style>
table,
td,
th {
  border: 1px solid #ddd;
  text-align: left;
}
.headerright h2 {
  font-weight: 600;
}
table {
  border-collapse: collapse;
  width: 100%;
}
th,
td {
  padding: 15px;
}
td a {
  color: blue;
}
.btn-primary {
  color: blue !important;
  border: unset !important;
}
td button {
  color: red !important;
  background: unset !important;
  border: 1px solid red;
}
.headerleft {
  float: left;
  width: 30%;
  padding-left: 10%;
  padding-top: 20px;
}
.headerright {
  float: left;
  width: 40%;
  padding-left: 2%;
  padding-top: 20px;
}
.headerright h3 {
  font-weight: 600;
  font-size: 20px;
  float: left;
  padding-bottom: 17px;
  padding-top: 0px;
}
header {
  float: left;
  width: 100%;
}
.item {
  border: 1px solid #000;
  text-align: center;
}
</style>