<template>
	   <div class="container">
      <div class="insideholder">
        <div class="item"></div>
        <div class="item"></div>
        <div class="item item1_3" :style="userStage[1] ===1 ? select : unselect">
          <img :src='"static/"+imgStatus[0]' class="xueliIcon" />
          <span :class="bingoStatus[0]"></span>
          <div class="time" :class="bingoStatus[0]==='bingoChecked'? '': 'sofar'">5分钟</div>
        </div>
        <div class="item item1_4" :style="userStage[1] ===1 ? select : unselect"></div>
        <div class="item item1_5" :style="userStage[2] ===1 ? select : unselect">
          <img :src='"static/"+imgStatus[1]' class="xueliIcon" />
          <span :class="bingoStatus[1]"></span>
          <div class="time" :class="bingoStatus[1]==='bingoChecked'? '': 'sofar'">10分钟</div>
        </div>
        <div class="item"></div>
        <div class="item item2_1"></div>
        <div class="item item2_2" :style="userStage[4] ===1 ? select : unselect">
          <img :src='"static/"+imgStatus[4]' class="xueliIcon" />
          <span :class="bingoStatus[4]"></span>
          <div class="time" :class="bingoStatus[4]==='bingoChecked'? '': 'sofar'">40分钟</div>
        </div>
        <div class="item item2_3" :style="userStage[4] ===1 ? select : unselect"></div>
        <div class="item item2_4" :style="userStage[3] ===1 ? select : unselect">
          <img :src='"static/"+imgStatus[3]' class="xueliIcon" />
          <span :class="bingoStatus[3]"></span>
          <div class="time" :class="bingoStatus[3]==='bingoChecked'? '': 'sofar'">30分钟</div>
        </div>
        <div class="item item2_5" :style="userStage[3] ===1 ? select : unselect"></div>
        <div class="item item2-6" :style="userStage[2] ===1 ? selectRight : unselectRight">
          <img :src='"static/"+imgStatus[2]' class="xueliIcon" />
          <span :class="bingoStatus[2]"></span>
          <div class="time" :class="bingoStatus[2]==='bingoChecked'? '': 'sofar'">20分钟</div>
        </div>
        <div class="item item3_1" :style="userStage[5] ===1 ? selectLeft : unselectLeft"></div>
        <div class="item item3_2" :style="userStage[6] ===1 ? select : unselect">
          <img :src='"static/"+imgStatus[5]' class="xueliIcon" />
          <span :class="bingoStatus[5]"></span>
          <div class="time" :class="bingoStatus[5]==='bingoChecked'? '': 'sofar'">50分钟</div>
        </div>
        <div class="item item3_3" :style="userStage[6] ===1 ? select : unselect"></div>
        <div class="item item3_4" :style="userStage[7] ===1 ? select : unselect">
          <img :src='"static/"+imgStatus[6]' class="xueliIcon" />
          <span :class="bingoStatus[6]"></span>
          <div class="time" :class="bingoStatus[6]==='bingoChecked'? '': 'sofar'">60分钟</div>
        </div>
        <div class="item item3_5" :style="userStage[7] ===1 ? select : unselect"></div>
        <div class="item item3_6">
          <img :src='"static/"+imgStatus[7]' class="xueliIcon" />
          <span :class="bingoStatus[7]"></span>
          <div class="time" :class="bingoStatus[7]==='bingoChecked'? '': 'sofar'">70分钟</div>
        </div>
        <div class="item item4_1"></div>
        <div class="item item4_2" :style="userStage[10] ===1 ? select : unselect">
          <img :src='"static/"+imgStatus[10]' class="xueliIcon" />
          <span :class="bingoStatus[10]"></span>
          <div class="time" :class="bingoStatus[10]==='bingoChecked'? '': 'sofar'">100分钟</div>
        </div>
        <div class="item item4_3" :style="userStage[10] ===1 ? select : unselect"></div>
        <div class="item item4_4" :style="userStage[9] ===1 ? select : unselect">
          <img :src='"static/"+imgStatus[9]' class="xueliIcon" />
          <span :class="bingoStatus[9]"></span>
          <div class="time" :class="bingoStatus[9]==='bingoChecked'? '': 'sofar'">90分钟</div>
        </div>
        <div class="item item4_5" :style="userStage[9] ===1 ? select : unselect"></div>
        <div class="item item4_6" :style="userStage[8] ===1 ? selectRight : unselectRight">
          <img :src='"static/"+imgStatus[8]' class="xueliIcon" />
          <span :class="bingoStatus[8]"></span>
          <div class="time" :class="bingoStatus[8]==='bingoChecked'? '': 'sofar'">80分钟</div>
        </div>
        <div class="item item5_1" :style="userStage[11] ===1 ? selectLeft : unselectLeft"></div>
        <div class="item item5_2" :style="userStage[11] ===1 ? select : unselect"></div>
        <div class="item item5_3" :style="userStage[12] ===1 ? select : unselect">
          <img :src='"static/"+imgStatus[11]' class="xueliIcon" />
          <span :class="bingoStatus[11]"></span>
          <div class="time" :class="bingoStatus[11]==='bingoChecked'? '': 'sofar'">110分钟</div>
        </div>
        <div class="item item5_4" :style="userStage[12] ===1 ? select : unselect"></div>
        <div class="item item5_5">
          <img :src='"static/"+imgStatus[12]' class="xueliIcon" />
          <span :class="bingoStatus[12]"></span>
          <div class="time" :class="bingoStatus[12]==='bingoChecked'? '': 'sofar'">120分钟</div>
        </div>
      </div>
      <div style="display:flex; align-items:center; justify-content:center">
        <input
          type="button"
          class="btn"
          :class="{cannotAcquire: totalMinutes === usedMinutes || usedMinutes > 120 || totalMinutes === 0}"
           :value="(totalMinutes === usedMinutes || usedMinutes > 120) ? btnText1 : btnText"
          @click='getXueLi(event)'
        />
      </div>
    </div>
</template>

<script>
export default {
  name:'',
  data() {
    return {
      unselect: "border-bottom:2px dashed #c0c0c0",
      select: "border-bottom:2px solid #f3b30b",
      unselectRight: "border: 2px dashed #c0c0c0;border-left:0px dashed;",
      selectRight: "border: 2px solid #f3b30b;border-left-width:0px; ",
      selectLeft: "border: 2px solid #f3b30b;border-right-width:0px;",
      unselectLeft: "border: 2px dashed #c0c0c0;border-right:0px dashed;",
      totalMinutes: 30,
      usedMinutes: 10,
      getAlready: [],
      bingoAlready: new Array(13).fill('bingo'),
	  btnText: "立即兑换",
	  btnText1: "已全兑换",
	  Icon: new Array(13).fill('notGet.png')
    };
  },
   computed: {
    userStage: function() {
		// 时长不够
		if(this.totalMinutes < 5){
				return this.getAlready;
			}
      //  1：路线变黄 undifined：路线为灰
      for (let i = 0; i <= this.totalMinutes / 10; i++) {
        this.getAlready[i] = 1;
      }
      return this.getAlready;
    },
    bingoStatus: function() {
		// 时长不够
		if(this.totalMinutes < 5){
				return this.bingoAlready;
			}
		for (let i = 0; i <= this.totalMinutes / 10; i++) {
        if (i <= this.usedMinutes / 10 && this.usedMinutes > 5) {
          //已经领取
          this.bingoAlready[i] = "bingoChecked";
        } else{
          this.bingoAlready[i] = "bingoTodo";
        }
      }
      return this.bingoAlready;
	},
	imgStatus:function(){
		if(this.totalMinutes < 5){
				return this.Icon;
			}
		for (let i = 0; i <= this.totalMinutes / 10; i++) {
        if (i <= this.usedMinutes / 10 && this.usedMinutes > 5) {
          //已经领取
          this.Icon[i] = "got.png";
        } else {
          this.Icon[i] = "getTodo.png";
        }
      }
      return this.Icon;
	}
  },
}
</script>

<style scoped>
.container {
  margin: 5%;
  background-color: white;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.insideholder {
  height: 500px;
  width:280px;
  margin: 0 30px 70px 30px;
  display: grid;
  grid-template-rows: 1fr 1fr 1fr 1fr 1fr;
  grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr;
}
.item {
  border-collapse: collapse;
  border-spacing: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}
.item2-6 {
  border-top-right-radius: 16px;
  border-bottom-right-radius: 16px;
  margin-top: -2px;
}
.item3_1 {
  border-top-left-radius: 16px;
  border-bottom-left-radius: 16px;
  margin-top: -2px;
}
.item4_6 {
  border-top-right-radius: 16px;
  border-bottom-right-radius: 16px;
  margin-top: -2px;
}
.item5_1 {
  border-top-left-radius: 16px;
  border-bottom-left-radius: 16px;
  margin-top: -2px;
}
.selectBorder {
  border-color: #f3b30b;
  border-style: solid;
}
.unselectBorder {
  border-color: #c0c0c0;
  border-style: dashed;
}
.bingo {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  position: absolute;
  background: rgba(255, 255, 255, 1);
  border: 2px solid rgba(226, 226, 226, 1);
  margin-top: 50px;
  margin-left: -18px;
}
.bingoTodo {
  width: 12px;
  height: 12px;
  border-radius: 12px;
  background: #f3b30b;
  display: block;
  position: absolute;
  margin-top: 50px;
  margin-left: -18px;
}
.bingoTodo:before,
.bingoTodo::after {
  content: "";
  height: 4px;
  width: 4px;
  border-radius: 50%;
  display: block;
  background: white;
  position: absolute;
  top: 4px;
  left: 4px;
  transform: rotate(45deg);
  -ms-transform: rotate(45deg);
}
.bingoChecked {
  width: 12px;
  height: 12px;
  border-radius: 12px;
  background: #f3b30b;
  display: block;
  position: absolute;
  margin-top: 50px;
  margin-left: -18px;
}

.bingoChecked:before,
.bingoChecked::after {
  content: "";
  height: 7px;
  width: 1px;
  display: block;
  background: white;
  position: absolute;
  top: 3px; /*40-6=34*/
  left: 7px; /*make the two rects in the middle of the cycle */
  transform: rotate(45deg);
  -ms-transform: rotate(45deg);
}
.bingoChecked::before {
  height: 4px;
  transform: rotate(-45deg);
  -ms-transform: rotate(-45deg);
  position: absolute;
  top: 6px; /*40-18=12  */
  left: 3px;
}
.inside {
  margin-top: 49px;
}
.time {
  position: absolute;
  margin-top: 70px;
  margin-left: -20px;
  font-size: 14px;
  font-family: PingFangSC-Regular;
  font-weight: 400;
  color: rgba(255, 185, 0, 1);
  line-height: 20px;
}
.sofar {
  font-size: 14px;
  font-family: PingFangSC-Regular;
  font-weight: 400;
  color: rgba(94, 94, 94, 0.7);
  line-height: 22px;
}
</style>
