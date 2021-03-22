<template>
  <div class="headeru">
    <search @getKeyWord="searchBlog" />
    <ListBlogs :dataBlogs="dataBlogs" @getListBlogs="searchAfterDelete" />
  </div>
</template>
<script>
   import axios from 'axios'
   import ListBlogs from '../../components/Blog/BlogList'
   import Search from '../../components/Blog/BlogSearch'
   export default {
      components: {
         Search,
         ListBlogs,
      },
      data() {
         return {
            dataBlogs: [],
            keySearch: '',
         }
      },
      methods: {
         /**
          * search blog by key search
          */
         searchBlog(data) {
            this.keySearch = data
            axios
               .get('http://localhost:4000/blogs' + '?title_like=' + data)
               .then((res) => {
                  this.dataBlogs = res.data
                  console.log(res.data)
               })
         },
         /**
          * reload list blog after delete
          */
         searchAfterDelete() {
            this.searchBlog(this.keySearch)
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
.headeru button {
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
.headeru {
  float: left;
  width: 40%;
  padding-left: 2%;
  padding-top: 20px;
}
.headeru label{
   position: relative;
   top:26px;
}
.headerright h3 {
  font-weight: 600;
  font-size: 20px;
}
.headeru h3 {
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
.headeru .headerright {
  width: 100% !important;
}
</style>