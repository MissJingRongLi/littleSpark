<template>
	<div class="cell" :class="{getBorder:this.getBor}">{{cName}}</div>
</template>

<script>
export default {
	props:['cName', 'getBor'],
  name:'',
  data(){
   return {
   }
  }
}
</script>

<style scoped>
.cell{
  width: 90%;
  height: 70px;
  display: flex;
  align-items: center;
  justify-content: flex-start;
  padding: 6px 12px 6px 5px;
  margin-left: 4%;
  border-bottom: 1px solid red;
}
.getBorder{
  background: rgba(182, 44, 53, 1);
  border: 2px solid rgba(226, 185, 85, 1);
  box-shadow: 0px 10px 16px 0px rgba(221, 89, 203, 0.2);
  border-radius: 5px;
}
</style>