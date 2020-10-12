<template>
  <div id="app">
    <Todo />
  </div>
</template>

<script>
import Todo from './components/Todo.vue'

export default {
  name: 'App',
  components: {
    Todo
  }
}
</script>

<style lang="less">
@import url('//at.alicdn.com/t/font_1489924_20vs2o2u8t9.css');
* {
  box-sizing: border-box;
}
</style>
