<template>
    <div class="container" @click='clickHandle'>
        <div class="message">{{msg}}</div>
        
         <!-- 使用 click-counter 组件 -->
    <!-- <click-counter :init-num="10" @clicknum="handleClickNum"> -->
        <!-- 填坑用... -->
        <input type="checkbox" /> 禁用
      <!-- </click-counter> -->

      <div>计数结果：{{count}}</div>
      <!-- <a href="/src/pages/logs/index.vue" class="navlink">进入计数器页面</a> -->
    </div>
</template>
<script>
    //导入click-counter 组件
    // import ClickCounter from "@/components/click-counter";
    //导入vuex
    // import globalStore from "../../stores/global-store";
export default {
      // 声明在当前组件下使用 counter-click 组件
  // components: { ClickCounter },
  computed: {
    count() {
      return globalStore.state.count;
    }
  },
    data(){
        return{
            msg:'欢迎来到魔兽世界'
        }
    },
    methods: {
        clickHandle(){
            this.msg='点击了我'
        },
        handleClickNum(data) {
      console.log(">>>>>>", data.num);
    }
    },
}
</script>
<style scoped>

.message{color: brown;padding: 10px;text-align: center;}
.navlink {
  text-decoration: underline;
}

</style>