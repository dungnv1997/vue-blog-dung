<template>
   <edit :title="title"></edit>
</template>
<script>
   import edit from '../../components/Blog/CreateEdit'
   export default {
       data() {
       return {
         title: 'Edit Blogs',
       } 
     },
       components: { 
           edit 
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
   margin-right: 0px;
   }
   label{
   float: left;
   width: 98%;
   padding-top: 15px;
   padding-left: 10px;}
   #checkbox2 {
   float: left;
   width: auto;
   margin-right: 0px;
   }
   .custom-checkbox input{
   width: auto;}
   .list-group-control input{
   margin-right: 0px;}
</style>