<template>
<div>
<AppHeader />
<AppMenu/>
  <div id="app" class="headerright">
	  <h2>Search Blog</h2>
      <div>Tiêu đề <input v-model="search" placeholder="tiêu đề"></div>
       <button type="button" placeholder="Tiêu đề.." class="btn btn-success"  @click="searchBlog()">Search</button><br>
      <Table v-if="showModal" />
       <table v-if="showModal1">
      <thead>

    <tr>

      <th 
>ID</th>

      <th >Tin</th>

      <th >Loại</th>

      <th >Trạng thái</th>

       <th >Vị trí</th>

      <th >Ngày public</th>

       <th >Edit</th>

      <th >Delete</th>

    </tr>

  </thead>
  <tbody>

     <tr  v-for="blogs in listBlog" :key="blogs.id">

                    <th scope="row">{{blogs.id}}</th>

                    <td>{{blogs.title}}</td>

                    <td>2</td>

                    <td>{{blogs.public}}</td>

                    <td>{{blogs.position}}</td>

                    <td>{{blogs.data_pubblic}}</td>

                    <td><nuxt-link :to="`/${blogs.id}`">Edit</nuxt-link></td>

                    <td><button type="button" class="btn btn -outline-danger" @click="deletedBlog(blogs.id)">Delete</button></td>

                </tr>
  </tbody>
    </table>
  </div>
  </div>
</template>



<script>

import AppHeader from '../components/AppHeader.vue'

import AppMenu from '../components/AppMenu.vue'

import Table from '../components/table-blog.vue'

import axios from 'axios'

export default {
  name: 'admin',

  components: {

    AppHeader,

    AppMenu, 

    Table

  },
  data() {

    return {

      listBlog: [],

      search: '',
      showModal: true,
      showModal1: false,

    }

  },
  methods: {

    searchBlog() {

      axios

        .get('http://localhost:4000/blogs' + '?title_like=' + this.search)

        .then((res) => {

          this.listBlog = res.data

          console.log(res.data)
            
        })
    this.showModal=false
    this.showModal1=true
    },
    deletedBlog(blogId){

       axios.delete('http://localhost:4000/blogs/' + blogId)

                .then(response => {

                    this.dataBlog.splice((blogId-1), 1)

                });

                console.log(this.dataBlog);

    }
  },

}

</script>



<style>

table, td, th {  
  border: 1px solid #ddd;
  text-align: left;
}
h2{
padding-bottom: 20px;}
input{
float: right;
border: 1px solid ;
width:80%;}
table {
  border-collapse: collapse;
  width: 100%;
}

th, td {
  padding: 15px;
}
.headerright button{
    margin-top:20px;
    margin-bottom: 20px;
    background: green;
    padding: 5px;
    color: #fff;
    border-radius: 5px;}
.headerleft{
  float: left;
    width: 30%;
    padding-left: 10%;
    padding-top: 20px;
}
.headerright{
  float: left;
    width: 40%;
    padding-left: 2%;
    padding-top: 20px;
}
.headerright h3{
      font-weight: 600;
    font-size: 20px;
}
header{
  float: left;
  width: 100%;
}
.item{
      border: 1px solid #000;
    text-align: center;
}
</style>
