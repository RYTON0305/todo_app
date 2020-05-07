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
        <li class="todo-item" v-for="item in 5" :key="item">
          <input :id="item" type="checkbox" />
          <label class="todo-item-icon" :for="item">
            <i class="iconfont icongou"></i>
          </label>
          <label class="todo-item-cotent" :for="item"
            >neirongneirong777777777777777777777777777777777777777777777777777777
          </label>
        </li>
      </ul>
      <div class="todo-footer">
        <div class="footer-count">一共有 0 个Todo</div>
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

<style lang="less">
body {
  width: 550px;
  max-width: 90vw;
  margin: 0 auto !important;
  transition: all ease 0.3s;
  &:hover {
    background-color: #cc9a9a;
    .title {
      color: #fff;
    }
  }
}
.title {
  font-size: 100px;
  // font-weight: 700;
  text-align: center;
  padding-top: 10px;
  color: #cc9a9a;
}

.main-box {
  margin: 20px auto 0;
  background-color: #fff;
  box-shadow: #aaa 0px 20px 35px -9px;
}
.todo-input {
  padding: 10px 60px;
  position: relative;
  height: 64px;

  border-bottom: 1px solid #ddd;
}
.input-box {
  width: 100%;
  height: 100%;
  outline: none;
  border: none;
  font-size: 20px;
  &::placeholder {
    font-style: italic;
    font-weight: 400;
    color: #ccc;
  }
}
.input-btn {
  width: 40px;
  height: 40px;
  position: absolute;
  right: 20px;
  top: 50%;
  transform: translateY(-50%);
  background-color: #cc9a9a;
  color: #fff;
  border: none;
  font-size: 30px;
  outline: none;
}

.todo-item {
  height: 60px;
  border-bottom: 1px solid #ddd;
  display: flex;
  align-items: center;
  padding-right: 10px;
  input {
    display: none;
  }
}
.todo-item-icon {
  border: solid 1px #ddd;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  line-height: 40px;
  text-align: center;
  margin: 0 10px;
  .icongou {
    color: lightgreen;
    font-size: 30px;
  }
}
.todo-item-cotent {
  height: 60px;
  padding: 0 10px;
  line-height: 60px;
  flex: 1;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
.todo-footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 10px;
  height: 50px;
  font-size: 14px;
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.2), 0 8px 0 -3px #f6f6f6,
    0 9px 1px -3px rgba(0, 0, 0, 0.2), 0 16px 0 -6px #f6f6f6,
    0 17px 2px -6px rgba(0, 0, 0, 0.2);
}
.footer-clear {
  color: #bbb;
  text-decoration: underline;
}
</style>
