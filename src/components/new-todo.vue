<template>
        <input v-model="taskName" name="add" placeholder="Nouvelle tâche...">
        <i v-on:click="counter +=1;sendTask()" class="fas fa-plus-circle"></i>
</template>

<script>
    export default {
        name: 'Todo',
        data () {
            
            return {
                taskname: "",
                counter: 0,
            }
        },
        methods: {
            sendTask() {
                this.$emit('newTask', this.taskName)
                this.$emit('counter', this.counter)
            }
        },
    }
</script>

<style>
  i {
      cursor: pointer;
      color: green;
      font-size: 60px;
      padding-left: 15px;

  }
  input {
      border: solid grey 1px;
      height: 60px;
      padding-right: 15px;
  }
  input::placeholder {
      font-size: 18px;
      text-align: center;
  }
</style>