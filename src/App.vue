<template>
  <p>count: {{count}}</p>
  <p>{{num}}</p>
  <!-- <button @click="count++">按钮</button> -->
  <button @click="handleClick">按钮</button>
</template>

<script>
import {reactive, toRefs, onMounted, onBeforeUnmount, onBeforeUpdate, ref} from 'vue'

/*
  https://vue3js.cn/docs/zh/guide/migration/introduction.html#%E6%A6%82%E8%A7%88

  setup() composition API入口 (在beforeCreate和created调用的)
  reactive() 定义响应式数据的方法
  toRefs() 展开响应式数据，可以单个使用
  生命周期
*/

export default {
  name: 'App',
  // data() {
  //   return {
  //     count: 0
  //   }
  // }
  // composition API入口
  setup() {

    console.log('setup', this); // 没有this
    
    // 定义单个响应式数据
    const num = ref(1)
    // 定义多个响应式数据
    const state = reactive({
      count: 0
    })
    
    const handleClick = () => {
      state.count++;
    }

    onBeforeUpdate(() => {
      console.log('onBeforeUpdate');
    })

    onMounted(() => {
      console.log('onMounted');
    })

    onBeforeUnmount(() => {
      console.log('onBeforeUnmount');
    })
    // console.log(toRef(state.count));
    // 返回值对象，会作为数据添加到this上
    return {
      // state,
      // count: toRef(state.count),
      ...toRefs(state), 
      handleClick,
      num
    }

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
