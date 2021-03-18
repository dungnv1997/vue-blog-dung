<template>

<BlogCreate></BlogCreate>

</template>



<script>

import BlogCreate from '@/components/BlogCreate.vue'

export default {

    components: {

        BlogCreate

    }

}

</script>

<style>
p{
width: 100%;
float: left;
padding-top: 10px;
    padding-bottom: 10px;
}
.btn-success{
width: 30%;}
.btn-primary{
width: 30%;
}
.headerright h3{
float: left;
    padding-top: 17px;
}
.blogNew input{
float: left;
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
</style>