<template>
  <div class="container">
    <div class="title">
      Todo list
    </div>

    <div class="main-box">
      <div class="todo-input">
        <input
          v-model="todoInput"
          type="text"
          placeholder="请输入Todo"
          class="input-box"
          @keypress.enter="addTodo"
        />
        <button class="input-btn" @click="addTodo">+</button>
      </div>
      <ul class="todo-list">
        <li class="todo-item" v-for="(item, index) in todoList" :key="index">
          <input
            :id="`todo${index}`"
            type="checkbox"
            v-model="item.completed"
            class="item-checkbox"
          />
          <label class="todo-item-icon" :for="`todo${index}`">
            <i
              class="iconfont icongou"
              :style="{ color: item.completed ? 'lightgreen' : '#fff' }"
            ></i>
          </label>
          <!-- <div
            v-if="item.editing"
            class="todo-item-cotent"
            :style="{
              textDecoration: item.completed ? 'line-through' : 'none',
              color: item.completed ? '#ccc' : '#000'
            }"
          >
            {{ item.content }}
          </div> -->
          <input class="todo-item-input" type="text" v-model="item.content" />
          <i class="iconfont iconxiugai item-editing"></i>
        </li>
      </ul>
      <div class="todo-footer">
        <div class="footer-count">一共有 {{ todoList.length }} 个Todo</div>
        <div class="footer-clear" @click="clearTodo">清除所有Todo</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Todo',
  data() {
    return {
      todoInput: '',
      todoList: JSON.parse(localStorage.getItem('todoList')) || []
    }
  },
  methods: {
    addTodo() {
      if (this.todoInput === '') {
        alert('请输入Todo')
      } else {
        this.todoList.push({
          content: this.todoInput,
          completed: false,
          editing: false
        })
        this.todoInput = ''
      }
    },
    clearTodo() {
      this.todoList = []
    },
    saveStorage() {
      localStorage.setItem('todoList', JSON.stringify(this.todoList))
    }
  },
  mounted() {
    // const todoList =
    // console.log(todoList)
    // if (todoList) {
    //   this.todoList = todoList
    // }
  },
  watch: {
    todoList: {
      handler() {
        this.saveStorage()
      },
      deep: true
    }
  }
}
</script>

<style lang="less">
body {
  width: 550px;
  max-width: 90vw;
  min-width: 320px;
  margin: 0 auto !important;
  transition: all ease 0.5s;
  &:hover {
    background-color: #cc9a9a;
    .title {
      color: #fff;
    }
    .input-btn {
      background-color: #cc9a9a;
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
  transition: all ease 0.5s;
}

.main-box {
  margin: 20px auto 30px;
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
  background-color: #fff;
  color: #cc9a9a;
  border: none;
  font-size: 30px;
  outline: none;
  transition: all ease 0.5s;
}

.todo-item {
  height: 60px;
  border-bottom: 1px solid #ddd;
  display: flex;
  align-items: center;
  padding-right: 10px;
  // overflow: hidden;
  position: relative;
  .item-checkbox {
    display: none;
  }
  .item-checkbox:checked ~ .todo-item-input {
    text-decoration: line-through;
    color: #aaa;
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
    transition: all ease 0.5s;
    color: #fff;
    font-size: 30px;
  }
}
// .todo-item-cotent,
.item-editing {
  display: none;
  padding-right: 10px;
  transition: 0.5s all ease;
  position: absolute;
  right: 20px;
}
.todo-item-input {
  height: 100%;
  padding: 0 10px;
  line-height: 60px;
  flex: 1;
  font-size: 20px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  border: none;
  outline: none;
  font-style: italic;
  transition: all ease 0.5s;
  &:focus {
    color: #bbb;
  }
  // &:hover + .item-editing {
  //   color: #ccc;
  //   display: block;
  // }
  &:focus + .item-editing {
    color: #cc9a9a;
    font-weight: 700;
    display: block;
  }
}
// .todo-edit-btn {
//   transition: 0.5s all ease;
//   display: none;
//   border: solid 1px #ddd;
//   width: 30px;
//   height: 30px;
//   border-radius: 50%;
//   text-align: center;
//   line-height: 30px;
//   margin: 0 10px;
//   color: #cc9a9a;
//   border-color: #cc9a9a;
//   background-color: #fff;
//   .iconfont {
//     font-size: 12px;
//     font-weight: 700;
//   }
// }
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
