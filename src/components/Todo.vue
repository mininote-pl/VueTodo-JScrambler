<template>
  <li class="list-group-item">
    <div class="row">
        <div class="col-md-8">
            <div class="todo-title" v-on:click="activateInEditMode" v-show="!isEditing" >
                {{ todo.title }}
            </div>
            <form v-show="isEditing" v-on:submit.prevent="deActivateInEditMode" >
                <div class="form-group">
                    <input v-model="todo.title" type="text" class="form-control" >
                </div>
            </form>
        </div>
        <div class="col-md-4">
            <span class="btn btn-default" v-on:click="removeTodo(todo)">remove</span>
            <span v-if="todo.done" class="bg-success todo-status">Done</span>
            <span v-else="todo.done" class="bg-danger todo-status">Not Done</span>
            <input v-model="todo.done" type="checkbox">
        </div>
    </div>
  </li>
</template>

<script>
export default {
  props: ['todo'],
  data () {
    return {
      isEditing: false
    }
  },
  methods: {
    activateInEditMode () {
      this.isEditing = true
    },
    deActivateInEditMode () {
      this.isEditing = false
    },
    removeTodo (todo) {
      this.$dispatch('remove-todo', todo)
    }
  }
}
</script>

<style scoped>
.todo-title {
    cursor: pointer;
    padding: 6px;
    margin-bottom: 15px;
}

.todo-title:hover {
    background-color: #F1EDED;
}
</style>
