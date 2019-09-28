<template>
  <view class="container">
    <Statusbar color="dodgerblue"/>
    <Header title="Todo App" />

    <view class="input-container">
      <text-input class="new-todo-text" v-model="newTodoText" />
      <touchable-opacity class="new-todo-btn" :on-press="() => newTodo()"> 
        <text class='btn-text'>Add</text> 
        </touchable-opacity>
    </view>

    <view class="todo" v-for="todo in todos" :key="todo.id">
     
      <touchable-opacity :style="{backgroundColor: todo.done ? 'red' : 'green'}"  class="todo-done-btn" :on-press="() => makeDone(todo.id)">
        <text class="todo-done-btn-text" v-if="todo.done">Undone</text>
        <text class="todo-done-btn-text" v-else>Done</text>
      </touchable-opacity>

      <text class="todo-title">{{todo.title}}</text>
     
      <touchable-opacity class="todo-remove-btn" :on-press="() => removeTodo(todo.id)">
        <text class="todo-remove-btn-text">X</text>
      </touchable-opacity>

    </view>
  </view>
</template>

<script>
  import Statusbar from './components/Statusbar'
  import Header from './components/Header'

  export default {
    data () {
      return {
        newTodoText: '',
        todos: [
          {
            id: 1,
            title: "Meu primeiro todo",
            done: false
          },
          {
            id: 2,
            title: "Meu segundo todo",
            done: false
          }
        ]
      }
    },
    components: {
      Header,
      Statusbar,
    },
    methods: {
      newTodo () {
        this.todos.push({
          id: Math.random(),
          title: this.newTodoText,
          done: false
        })
        this.newTodoText = ''
      },
      removeTodo (id) {
        this.todos = this.todos.filter(todo => todo.id !== id)
      },
      makeDone (id) {
        this.todos = this.todos.map(todo => {
          if(todo.id === id) todo.done = !todo.done
          return todo
        })
      }
    }
  }
</script>

<style>
  .container {
    background-color: white;
    flex: 1;
  }

  .input-container {
    margin: 5px;
    flex-direction: row;
    justify-content: center;
    align-items:stretch;
  }

  .new-todo-text {
    background-color: #999;
    flex: 1;
    height: 40px;
    padding: 0 5px;
  } 

  .new-todo-btn {
    background-color: dodgerblue;
    color: white;
    margin-left: 10px;
    height: 40px;
    width: 40px;
    align-items: center;
    justify-content: center;
  } 

  .btn-text {
    font-weight: bold;
    font-size: 12px;
    color: white;
  }
  
  .todo {
    height: 50px;
    width: 100%;
    justify-content: space-between;
    align-items: center;
    flex-direction: row;
    padding: 10px;
    margin: 5px 0px;
  }

  .todo-remove-btn {
    background-color: red;
    width: 20px;
    justify-content: center;
    align-items: center;
    border-radius: 3px;
  }

  .todo-remove-btn-text {
    color: white;
  }

  .todo-done-btn {
    height: 100%;
    padding: 5px;
    border-radius: 3px;
  }

  .todo-done-btn-text {
    color: white;
  }
</style>
