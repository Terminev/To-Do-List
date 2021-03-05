<template>
    <div class="addtask">
        <input v-model.trim="taskName" name="add" placeholder="Nouvelle tâche...">
        <i v-on:click="sendTask()" class="fas fa-plus-circle"></i>

    </div>
</template>

<script>
    export default {
        name: 'Todo',
        data() {

            return {
                taskName: "",
                counter: 0,
            }
        },
        methods: {
            sendTask() {
                if (this.taskName != ""){
                this.counter+=1
                this.$emit('sendTask', this.taskName)
                this.$emit('counter', this.counter)
                
            }
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
        text-align: center;
    }

    input::placeholder {
        font-size: 18px;
        text-align: center;
    }

    .addtask {
        display: flex;
        justify-content: center;
    }
</style>