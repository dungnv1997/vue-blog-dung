<template>

  <div>
        <AppHeader />
<AppMenu/>
        <div class="headerright">
          <div class="col-sm-9">

            <div class="blogNew">

                <h3>New Blog</h3>

                <p>Tiêu đều</p>

                <input type="text" style="width: 50%;" v-model="form.title">

                <p>Mô tả ngắn</p>

                <input type="text" style="width: 50%;"  v-model="form.des">

                <p>chi tiết</p>

                <textarea name="" id="" cols="30" rows="10" style="width: 50%;" v-model="form.detail"></textarea>

                <p>Hình ảnh </p>

                <input type="file" name="thumps" id="" />

                <p>Loại</p>

                 <select name="type" id="type" v-model="form.category">

                <option v-for="(cat, index) in CATEGORY" :key="index" :value="cat.id">

                    {{ cat.name }}

                </option>

                </select>

                <p>Vị trí</p>

                <ul class="list-group list-group-flush list-unstyled">

                    <li

                        v-for="(post, key) in POSITION"

                        v-bind:key="post"

                        class="list-group-control"

                    >

                        <div class="custom-control custom-checkbox">

                        <input

                            type="checkbox"

                            :value="key"

                            class="custom-control-input"

                            :id="'check' + key"

                            v-model="form.position"

                        />

                        <label class="custom-control-label" :for="'check' + key">{{

                            post

                        }}</label>

                        </div>

                    </li>

                    </ul>

                <p>Public</p>
                <input type="radio" id="checkbox1" name="yes" :value="true" v-model="form.public"><label for="checkbox1">Yes</label><br>

                <input type="radio" id="checkbox2" name="no" :value="false" v-model="form.public"><label for="checkbox2">No</label><br>
                
                <p>Date Public</p>

                <input type="date" name="" id="" v-model="form.data_pubblic">


                <button type="button" class="btn btn-success1" @click="updateBlog(form.id)">Submit</button>

                <button type="button" class="btn btn-primary1">Clear</button>

            </div>  

          </div>

        </div>  

    </div>

</template>
<script>

import AppHeader from '../components/AppHeader.vue'

import AppMenu from '../components/AppMenu.vue'

import Table from '../components/table-blog.vue'

import axios from 'axios'

const CATEGORY = [

  { id: 1, name: 'thời sự' },

  { id: 2, name: 'thế giới' },

  { id: 3, name: 'kinh doanh' },

  { id: 4, name: 'giải trí' },

  { id: 5, name: 'thời sự' },

  { id: 6, name: 'thế giới' },

  { id: 7, name: 'kinh doanh' },

  { id: 8, name: 'giải trí' },

  { id: 9, name: 'thời sự' },

]

const POSITION = ['Việt Nam', 'Châu Á', 'Châu Âu', 'Châu Mỹ']

export default {

  props: ['title'],

  name: 'New',

  data() {

    return {

      CATEGORY,

      POSITION,

      form: {

        id: '',

        title: '',

        des: '',

        detail: '',

        category: '',

        public: '',

        data_pubblic: '',

        position: [],

        thumbs: '',

      },

    }

  },

  methods: {

    createBlog() {

      axios.post('http://localhost:4000/blogs', this.form).then((res) => {

        alert('thêm thành công')

      })

      this.$router.push('/blog/list')

    },

    getBlogByID(id) {

      axios

        .get('http://localhost:4000/blogs/' + id)

        .then((res) => (this.form = res.data))

    },

    updateBlog(id) {

      axios.put('http://localhost:4000/blogs/' + id, this.form).then((res) => {

        // alert('thêm thành công')

      })

      this.$router.push('/list')

    },

  },

  mounted() {

      this.getBlogByID(this.$route.params.id)

  },

}

</script>
<style>
p{
width: 100%;
float: left;
padding-top: 10px;
    padding-bottom: 10px;
}
.btn-success1{
width: 30%;}
.btn-primary1{
width: 30%;
}
.headerright h3{
float: left;
    padding-top: 17px;
}
.blogNew input{
float: left;
width: 50%;
margin-right: 50%;
margin-top: 20px;}
textarea{
border: 1px solid;}
select{
float: left;
border: 1px solid;}
li{
    float: left;
    width: 100%;}
    #checkbox1{
    float: unset;
    }
    .headerright button {
    margin-top: 20px;
    margin-bottom: 20px;
    background: green;
    padding: 5px;
    color: #fff;
    border-radius: 5px;
}
#checkbox1 {
    float: left;
    width: auto;
}
label{
    float: left;
    width: 98%;
    padding-top: 15px;
    padding-left: 10px;}
#checkbox2 {
    float: left;
    width: auto;
}
.custom-checkbox input{
width: auto;}

</style>