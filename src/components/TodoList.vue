<template>
  <div class="app">
    <input type="text" class="todo-input" 
    placeholder="What needs to be done"
    v-model="newTodo" @keyup.enter="addTodo"/>

    <transition-group enter-active-class="animated fadeInUp"
    leave-active-class="animated fadeOutDown">
        <todo-item v-for="(todo, index) in todosFiltered"
        :key="todo.id" :todo="todo" :index="index" :checkAll="!anyRemaining"
        >
        </todo-item>
    </transition-group>
    <div class="extra-container">
        <TodoCheckAll>
        </TodoCheckAll>
        <TodoItemsRemaining>
        </TodoItemsRemaining>
    </div>

     <div class="extra-container">
        <TodoFiltered></TodoFiltered>

      <div>
        <transition name="fade">
            <TodoClearCompleted>
            </TodoClearCompleted>
        </transition>
      </div>
    </div>
    
  </div>
</template>

<script>
import TodoItem from './TodoItem'
import TodoItemsRemaining from './TodoItemsRemaining'
import TodoCheckAll from './TodoCheckAll'
import TodoFiltered from './TodoFiltered'
import TodoClearCompleted from './TodoClearCompleted'

export default {
  name: 'TodoList',
  
  components: {
      TodoItem,
      TodoItemsRemaining,
      TodoCheckAll,
      TodoFiltered,
      TodoClearCompleted
  },

  data () {
      return {
          newTodo: '',
          idForTodo: 3,
          beforeEditCache: '',
          
      }
    },
    computed: {
        remaining() {
            return this.$store.getters.remaining;
        },
        anyRemaining() {
            return this.$store.getters.anyRemaining;
        },
        todosFiltered() {
           return this.$store.getters.todosFiltered;
        },
        showClearCompletedButton() {
            return this.$store.getters.showClearCompletedButton;
        }
    },
    methods: {
        addTodo() {
            if (this.newTodo.trim().lenght == 0) {
                return;
            }
            this.$store.dispatch('addTodo', {
                id: this.idForTodo,
                title: this.newTodo,
            })
            this.newTodo = '';
            this.idForTodo++;
        },
    }
}
</script>

<style>
    @import './TodoList.css';
</style>
