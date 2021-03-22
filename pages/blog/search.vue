<template>
  <div>
    <div id="app" class="headerright">
      <BlogSearch @button-clicked="searchBlog"></BlogSearch>
      <Table v-if="ListNotSearch" />
      <table v-if="ListSearch">
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
          <tr v-for="blogs in listBlog" :key="blogs.id">
            <th scope="row">{{ blogs.id }}</th>
            <td>{{ blogs.title }}</td>
            <select name="type" id="type" v-model="form.category">
              <option
                v-for="(cat, index) in CATEGORY"
                :key="index"
                :value="index"
              >
                {{ cat }}
              </option>
            </select>
            <td>{{ blogs.public }}</td>
            <td>{{ blogs.position }}</td>
            <td>{{ blogs.data_pubblic }}</td>
            <td>
              <nuxt-link :to="`/${blogs.id}`">Edit</nuxt-link>
            </td>
            <td>
              <button
                type="button"
                class="btn btn -outline-danger"
                @click="deleteBlog(index, blogs.id)"
                onclick="return confirm('Bạn có muốn xóa ?')"
              >
                Delete
              </button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
<script>
   import Table from '../../components/Blog/TableBlog' 
   import BlogSearch from '../../components/Blog/BlogSearch'
   import axios from "axios";
   export default {
     name: "admin",
     components: {
       Table,
       BlogSearch
     },
     data() {
       return {
         listBlog: [],
         search: "",
         ListNotSearch: true,
         ListSearch: false
       };
     },
     methods: {
       searchBlog(data) {
         axios
           .get("http://localhost:4000/blogs" + "?title_like=" + data)
           .then(res => {
             this.listBlog = res.data;
             console.log(res.data);
           });
         this.ListNotSearch = false;
         this.ListSearch = true;
       },
       deleteBlog(index, id) {

      axios.delete('http://localhost:4000/blogs/' + id).then((res) => {
        console.log('deleted successfully')
        this.dataBlog.splice(index, 1)
      })
    }
     }
   };
</script>
<style>
table,
td,
th {
  border: 1px solid #ddd;
  text-align: left;
}
h2 {
  padding-bottom: 20px;
}
input {
  float: right;
  border: 1px solid;
  width: 80%;
}
table {
  border-collapse: collapse;
  width: 100%;
}
th,
td {
  padding: 15px;
}
.headerright button {
  margin-top: 20px;
  margin-bottom: 20px;
  background: green;
  padding: 5px;
  color: #fff;
  border-radius: 5px;
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