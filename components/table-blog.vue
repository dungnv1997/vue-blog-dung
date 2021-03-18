<template>
    <table>
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

     <tr  v-for="blogs in dataBlog" :key="blogs.id">

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
</template>

<!-- <script>
export default {
	async asyncData({ $content, params }) {
		const articles = await $content('articles', params.slug)
			.only(['id','title', 'category', 'public','position','data_pubblic','slug'])
			.sortBy('createdAt', 'asc')
			.fetch();
		return {
			articles
		}
	}
}
</script> -->
<script>

import axios from 'axios'

export default {

  components : {

  },

  data(){

    return {

      dataBlog : [],

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

    deletedBlog(blogId){

       axios.delete('http://localhost:4000/blogs/' + blogId)

                .then(response => {
                  

                    this.dataBlog.splice((blogId-1), 1)

                });

                console.log(this.dataBlog);

    }

  }

}



</script>

<style>
table, td, th {  
  border: 1px solid #ddd;
  text-align: left;
}
.headerright h2{
 font-weight: 600;
}
table {
  border-collapse: collapse;
  width: 100%;
}

th, td {
  padding: 15px;
}
td a{
color:blue;}
td button{
 color: red !important;
 background: unset!important;
 border: 1px solid red;
}
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
