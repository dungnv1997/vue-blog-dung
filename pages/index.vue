<template>
  <div class="headerright">
	  <h2>List Blog</h2>
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

    <tr v-for="article of articles" :key="article">

      <th scope="row">{{article.id}}</th>

      <td>{{article.title}}</td>

      <td>{{article.category}}</td>

      <td>{{article.public}}</td>

       <td>{{article.position}}</td>

      <td>{{article.data_pubblic}}</td>

      <td><a href="" class="btn btn-primary">Edit</a></td>

          <td><a href="" class="btn btn-danger">Delete</a></td>
    </tr>
  </tbody>
    </table>
  </div>
</template>

<script>
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
</script>

<style>
table, td, th {  
  border: 1px solid #ddd;
  text-align: left;
}

table {
  border-collapse: collapse;
  width: 100%;
}

th, td {
  padding: 15px;
}
.headerleft{
  float: left;
    width: 30%;
    padding-left: 10%;
    padding-top: 20px;
}
.headerright{
  float: left;
    width: 70%;
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
