<template>
  <div class="container">
    <Cell v-for="(item) in list" :key="item.id" :cName="item.name"
			:getBor='item.id === id'></Cell>
  </div>
</template>

<script>
import Cell from "Cell";
export default {
  name: "",
  data() {
    return {
      listAll: [
        { id: 1, name: "zhangsan1" },
        { id: 2, name: "zhangsan2" },
        { id: 3, name: "zhangsan3" },
        { id: 4, name: "zhangsan4" },
        { id: 5, name: "zhangsan5" },
        { id: 6, name: "zhangsan6" },
        { id: 7, name: "zhangsan7" },
        { id: 8, name: "zhangsan8" },
      ],
	  id: -1,
	  list:[],
    };
  },
  mounted() {
    this.keyup();
  },
  methods: {
    keyup() {
		// 一次显示三组数据
		this.list = this.listAll.slice(0,3)
      document.onkeydown = e => {
        if (this.list.length > 0) {
          //返回有数据
          // 向下翻动效果
          if (e.keyCode == 40) {
			  this.id++
			  // 不在初始化的List中
            if (this.id > 3 && this.id <= this.listAll.length) {
			  this.list = this.listAll.slice(this.id - 3, this.id);
            }else if(this.id > this.listAll.length){
				this.id = this.listAll.length
				return 
			}
          }
          //向上翻动效果
          else if (e.keyCode == 38) {
			  this.id--
			  //已经在最顶部
            if (this.id == -1) {
              return
            }
            //不在初始化的showList中
            if (this.id > 3 && this.id <= this.listAll.length) {
              this.list = this.listAll.slice(this.id - 3, this.id);
            } else if (this.id <= 3) {
              this.list = this.listAll.slice(0, 3);
              if (this.id <= 0) {
                this.id = 0;
              }
		  }
		  }
        }
      };
    }
  },
  components: {
    Cell
  }
};
</script>

<style scoped>
.container {
  width: 300px;
  height: 400px;
  display: flex;
  flex-direction: column;
}
</style>