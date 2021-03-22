<template>
  <table>
    <thead>
      <tr>
        <th>ID</th>
        <th>Tin</th>
        <th>Loại</th>
        <th>Trạng thái</th>
        <th>Vị trí</th>
        <th>Ngày public</th>
        <th>Edit</th>
        <th>Delete</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="blogs in dataBlog" :key="blogs.id">
        <th scope="row">{{ blogs.id }}</th>
        <td>{{ blogs.title }}</td>
        <td>
            <div v-for="(cate, index) in CATEGORY" :key="index">
              <p v-if="getNamCatalog(index,blogs.category)">{{ cate }}</p>
            </div>
        </td>
        <td>{{ blogs.public == true ? "yes" : "no" }}</td>
        <td>{{ filterPosition(blogs.position) }}</td>
        <td>{{ blogs.data_pubblic }}</td>
        <td>
          <nuxt-link :to="`/blog/${blogs.id}`">Edit</nuxt-link>
        </td>
        <td>
          <button
            type="button"
            class="btn btn -outline-danger"
            @click="deleteBlog(index, blogs.id)"
            onclick="return confirm('you may want to delete ?')"
          >
            Delete
          </button>
        </td>
      </tr>
    </tbody>
  </table>
</template>
<script>
   import axios from 'axios' 
   import { DATA_CATE } from '@/content/content.js'
   import { DATA_POS } from '@/content/content.js'
   export default {
     components : {
     },
     data(){
       return {
         dataBlog : [],
         POSITION: DATA_POS,
         CATEGORY:DATA_CATE, 
         form :{

         }
       }
     },
     mounted() {
       this.listData();
     },
     computed: {
     },
     methods:{
       listData(){
         axios({method: 'GET',url: 'http://localhost:4000/blogs',data: null}).then(res =>{this.dataBlog = res.data; console.log(this.data)
         }).catch(err => {console.log(err)})
       }, 
      deleteBlog(index, id) {
      axios.delete('http://localhost:4000/blogs/' + id).then((res) => {
        console.log('xoa thanh cong')
        this.dataBlog.splice(index, 1)
      })
    },
    /**
     * get name position
     */
     filterPosition(pos) {
      return pos
        .map((item) => {
          return this.POSITION[item];
        })
        .join(",");
    },
     /**
     * get name catalog
     */
    getNamCatalog(a,b){
      if(a!=b) return false;
      return true;
    }
    
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