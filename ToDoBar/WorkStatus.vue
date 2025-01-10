<template>
  <div>
    <div class="container">
      <!-- 第一列 -->
<!--      <div class="column1">-->
<!--        <img src="@/assets/icons/img.png" />-->
<!--      </div>-->

      <!-- 第二列 -->
      <div class="column2">
        <!-- 第二列的第一行 -->
        <div class="row spacer">
          <el-row class="title">
            <el-col :span="22">
              {{ formDataNew.subject }}
            </el-col>
            <el-col :span="2" class="right-align">
              <el-link type="info" :href="formDataNew.url" target="_blank" style="font-size:14px">详情</el-link>
            </el-col>
          </el-row>
        </div>

        <!-- 第二列的第二行 -->
        <div class="row">
          <el-row class="content">
            <el-col :span="4" style="color: rgb(0, 128, 0)">
              <span style="margin-left:5px"> 发起时间:&nbsp</span>
              <i class="el-icon-date" />
              <span style="margin-left:5px">{{convertTimestamp(formDataNew.finishTime)}}</span>
            </el-col>

            <el-col :span="4" style="color: rgb(252, 79, 45)">
              <span style="margin-left:5px">{{abc(formDataNew.status,formDataNew.finishTime)}}</span>
            </el-col>

            <el-col :span="12" class="content-text" style="word-wrap:break-word;">
              <i class="el-icon-thumb" style="transform: rotate(90deg);" />
              <span style="margin-left:5px">
              </span>
              {{ formDataNew.creator}} 指派给{{formDataNew.receiver }}
            </el-col>
          </el-row>
        </div>
      </div>

    </div>
    <el-divider class="divider" />
  </div>

</template>
<script>
export default {
  props: {
    formDataNew: {
      type: Object,
      default() {
        return {}
      },
    },
  },
  data() {
    return {

    }
  },
  methods: {
    abc(status,timestamp){
      console.log('啦啦啦啦')
      if(status === 'SUCCESS' || status === 'FAILED'){
        return '已完成';
      }
      return '已等待: '+ this.diffCalculate(timestamp)
    },
    diffCalculate(timestamp) {
      const diff = Date.now() - timestamp;
      const days = Math.floor(diff / (1000 * 60 * 60 * 24));
      const hours = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
      const minutes = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60));
      const res = `${days} 天 ${hours} 小时 ${minutes} 分钟`;
      return res;
    },
    convertTimestamp(timestamp) {
      const date = new Date(timestamp);
      const year = date.getFullYear();
      const month = date.getMonth() + 1;
      const day = date.getDate();
      const hours = date.getHours();
      const minutes = date.getMinutes();
      const seconds = date.getSeconds();

      const formattedTime = `${year}-${month}-${day} ${hours}:${minutes}:${seconds}`;
      return formattedTime;
    }
  },
}
</script>

<style scoped>
.container {
  display: flex;
  width: 100%;
}

.column1,
.column2 {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: left;
  padding: 10px;
}

.column1 {
  flex: 1;
  flex-basis: 1%;
  /* 设置左边列的初始宽度为整个容器的 1% */
}

.column2 {
  flex: 9;
}


.spacer {
  margin-bottom: 6px;
}

.title {
  font-size:14px;
  font-weight: 500;
}

.right-align {
  display: flex;
  /*justify-content: flex-end;*/
  color: rgb(139, 138, 138);
  /* 将内容右对齐 */
}

img {
  width: 80px;
}

.content {
  font-size: 12px;
  margin-top: 8px;
  font-weight: 500;
}

.content-text {
  color: rgb(139, 138, 138);
}


.divider {
  margin: 0 auto 15px;
}
</style>
