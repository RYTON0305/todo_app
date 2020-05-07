<template>
  <div class="container">
    <div class="title">
      Todo list
    </div>

    <div class="main-box">
      <div class="todo-input">
        <input type="text" placeholder="请输入Todo" class="input-box" />
        <button class="input-btn">+</button>
      </div>
      <ul class="todo-list">
        <li class="todo-item"></li>
      </ul>
      <div class="todo-footer">
        <div class="footer-count">一共有0个Todo</div>
        <div class="footer-clear">清除所有Todo</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Todo'
}
</script>

<style scoped lang="less"></style>
