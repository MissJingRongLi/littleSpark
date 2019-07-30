<template>
  <div class="container" @mouseenter="stopAutoPlay" @mouseleave="autoPlay">
    <div class="wrap" style="left:-300px">
      <!-- 隐藏掉列出的第一个img元素，实现从第一张图片开始 -->
      <img src="../assets/logo5.jpg" />
      <img src="../assets/logo1.png" />
      <img src="../assets/logo2.jpg" />
      <img src="../assets/logo3.jpg" />
      <img src="../assets/logo4.jpg" />
      <img src="../assets/logo5.jpg" />
      <img src="../assets/logo1.png" />
    </div>
    <div class="buttons">
      <span :class="select[0]">1</span>
      <span :class="select[1]">2</span>
      <span :class="select[2]">3</span>
      <span :class="select[3]">4</span>
      <span :class="select[4]">5</span>
    </div>
    <a href="javascript:;" class="arrow arrow_left" @click="getPrev">&lt;</a>
    <a href="javascript:;" class="arrow arrow_right" @click="getNext">&gt;</a>
  </div>
</template>

<script>
export default {
  name: "",
  data() {
    return {
      wrap: document.getElementsByClassName("wrap"),
      timer: null,
      dots: document.getElementsByTagName("span"),
      index: 0
    };
  },
  computed: {
    select() {
      var arr = [];
      for (var i = 0; i < 5; i++) {
        if (i === this.index) {
          arr[this.index] = "on";
        } else {
          arr[i] = "";
        }
      }
      return arr;
    }
  },
  methods: {
    autoPlay() {
      this.timer = setInterval(this.getNext, 2000);
    },
    stopAutoPlay() {
      clearInterval(this.timer);
    },
    // 为了实现更好的可复用性，可以将newLeft的数值使用计算的方式给出
    // 当向右翻到达最后一张照片时（也就是第一张），跳转至正数第二张
    // 当向左翻到达最后一张照片时（也就是最后一张），跳转至倒数第二张
    getPrev() {
      var newLeft;
      if (this.wrap[0].style.left === "0px") {
        newLeft = -1200;
      } else {
        newLeft = parseInt(this.wrap[0].style.left || 0) + 300;
      }
      this.index--;
      if (this.index < 0) {
        this.index = 4;
      }
      this.wrap[0].style.left = newLeft + "px";
    },
    getNext() {
      var newLeft;
      if (this.wrap[0].style.left === "-1800px") {
        newLeft = -600;
      } else {
        newLeft = parseInt(this.wrap[0].style.left || 0) - 300;
      }
      this.index++;
      if (this.index > 4) {
        this.index = 0;
      }
      this.wrap[0].style.left = newLeft + "px";
    },
    // 显示下方小圆点的变化选中当前哪张图片
    showCurrent() {
      for (var i = 0; i < this.dots.length; i++) {
        if (i === this.index) {
          this.dots[index].className = "on";
        } else {
          this.dots[i].className = "";
        }
      }
    }
  },
  mounted() {
    this.autoPlay();
  }
};
</script>

<style scoped>
/* 需要对body进行居中处理 */
.container {
  width: 300px;
  height: 300px;
  position: relative;
  overflow: hidden;
}
a {
  text-decoration: none;
}
.wrap {
  width: 2100px;
  position: absolute;
  display: flex;
  align-items: center;
  justify-content: center;
}
img {
  width: 300px;
  height: 300px;
  float: left;
}

.buttons {
  bottom: 10px;
  position: absolute;
  /* 宽度继承父元素 与img宽度一致 */
  width: 100%;
  display: flex;
  justify-content: space-around;
}
span {
  margin-left: 5px;
  display: inline-block;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background-color: green;
  text-align: center;
  color: white;
  cursor: pointer;
}
span.on {
  background-color: red;
}
.arrow {
  position: absolute;
  top: 35%;
  color: green;
  border-radius: 50%;
  font-size: 50px;
}
.arrow_left {
  left: 10px;
}
.arrow_right {
  right: 10px;
}
/* 鼠标放上去的效果 */
.container .arrow:hover {
  background-color: rgba(0, 0, 0, 0.2);
}
</style>
