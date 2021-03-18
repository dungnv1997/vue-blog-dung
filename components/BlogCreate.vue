<template>

  <div>
<AppHeader />
<AppMenu/>
        <div class="headerright">
          <div class="col-sm-9">

            <div class="blogNew">

                <h3>New Blog</h3>

                <p>Tiêu đều</p>

                <input type="text" style="width: 50%;" >

                <p>Mô tả ngắn</p>

                <input type="text" style="width: 50%;" >

                <p>chi tiết</p>

                <textarea name="" id="" cols="30" rows="10" style="width: 50%;" ></textarea>

                <p>Hình ảnh </p>

                <input type="file" name="thumps" id="" />

                <p>Loại</p>

                <select >

                <option value="1">Thời Sự</option>

                <option value="2">Kinh Doanh</option>

                <option value="3">Thế Giới</option>

                <option value="4">Thể Thao</option>

                </select>

                <p>Vị trí</p>

                <ul class="list-group list-group-flush">

                  <li  class="list-group-control">

                 viet nam

                  </li>
                  <li  class="list-group-control">

                 lao

                  </li>

                </ul>

                <p>Public</p>

                <input type="radio" id="checkbox1" name="yes" :value="true" ><label for="checkbox1">Yes</label><br>
               
                <input type="radio" id="checkbox2" name="no" :value="false" ><label for="checkbox2">No</label><br>
        
                <p>Date Public</p>

                <input type="date" name="" id="">

                <br><br><br>

                <button type="button" class="btn btn-success" @click="submit" onclick="location.href='/list'">Success</button>

                <button type="button" class="btn btn-primary">Primary</button>

            </div>  

          </div>

        </div>  

    </div>

</template>
<script>

import AppHeader from '../components/AppHeader.vue'

import AppMenu from '../components/AppMenu.vue'

import Table from '../components/table-blog.vue'

export default {

  name: 'admin',

  components: {

    AppHeader,

    AppMenu, 

    Table

  }

}
</script>
