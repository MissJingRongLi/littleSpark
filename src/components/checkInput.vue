<template>
	<div>
		<h3>input 框处理防抖和中文输入</h3>
	<div>
		<input type='text' id='myInput'>
	</div>
	</div>
</template>

<script>
export default {
  name:'',
  data(){
   return {
	   flag: '',
   }
  },
  computed:{
	//   使用计算属性能够提前获取到相关的数据
	  myInput:function(){
		  return document.getElementById('myInput')
		  }
  },
  methods:{
	 debounce: function(){
		// timeOut要定义在外面实现闭包
		let timeOut = null
		return function(value,wait){
			clearTimeout(timeOut)
			timeOut = setTimeout(()=>{
				console.log(value)
			}, wait)
		}
	},
  },
  mounted(){
	  var resFunc = this.debounce() 
	  this.myInput.addEventListener('input',(e)=>{
		// 添加防抖函数 在一定时间内没有再次触发才会执行相应的处理函数
		// console.log(e.target.value)
		if(this.flag === 'end' || ''){
			// 中文输入结束后才触发
			resFunc(e.target.value, 1000)
		}
	})
	  this.myInput.addEventListener('compositionstart',(e)=>{
		  this.flag = 'start'
		console.log('中文开始')
	})
	// myInput.addEventListener('compositionupdate',(e)=>{
	// 	console.log(e.target.value)
	// })
	this.myInput.addEventListener('compositionend',(e)=>{
		this.flag = 'end'
		console.log('中文结束')
		resFunc(e.target.value, 1000)
	})
  }
}
</script>

<style scoped>

</style>
