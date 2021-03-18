<template>
<div>
<AppHeader />
<AppMenu/>
 <div class="headerright">
	  <h2>List Blog</h2>
     <Table :dataBlogs="dataBlogs" />
</div>
</div>
</template>

<script>
import axios from 'axios'
import AppHeader from '../components/AppHeader.vue'

import AppMenu from '../components/AppMenu.vue'

import Table from '../components/table-blog.vue'

export default {

  name: 'admin',

  components: {

    AppHeader,

    AppMenu, 

    Table

  },
  data() {

    return {

      dataBlogs: [],

    }

  },

  methods: {

    getData() {

      axios.get('http://localhost:4000/blogs').then((res) => {

        this.dataBlogs = res.data

        console.log(this.dataBlogs)

      })

    },

  },

  mounted() {

    this.getData()

  },

}

</script>
