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
@import url('//at.alicdn.com/t/font_1489924_vkiz6mk5fan.css');
* {
  box-sizing: border-box;
}
</style>
