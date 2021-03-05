<template>
    <div>
        <ul>
            <li class="nametasks" v-for="(task, index) in task" :key="(task, index)">
                <input type="checkbox" v-on:click='check(index)'>
                <h3 v-bind:class="{'end':task.checked}">{{ task.description}}</h3>
                <i class="fas fa-trash" v-on:click="addition +=-1;remover(index)"></i>
            </li>
        </ul>
     <div v-if="addition > 1">
            <button class="CtaDel" v-on:click="deleteAll">Vider les Tâches</button>
    </div>
    </div>
</template>
<script>
    export default {
        name: "TodoList",
        props: ['task'],
        methods: {
            check(index) {
                this.$emit('endtask', index)
            },
            remover(index) {
                this.$emit('deletetask', index)
            },
            deleteAll(index) {
                this.$emit('deleteall', index)
            }

        }
    }
</script>
<style scoped>
    .end {
        text-decoration: line-through;
        color: red;
    }

    .nametasks {
        display: flex;
        align-items: center;
        width: 80%;
        justify-content: space-between;
        margin: 0 auto;
        margin-top: 25px;
    }

    .nametasks h3 {
        font-size: 22px;
    }

    .nametasks input {
        width: 20px;
        height: 20px;
    }

    .CtaDel {
        margin-top: 25px;
        border: none;
        background-color: green;
        padding: 10px 20px;
        font-size: 18px;
        border-radius: 10px;
        color: white;
        font-weight: bold;
    }

    .fa-trash {
        color: white;
        padding: 19px 20px;
        border-radius: 30px;
        background-color: red;
        font-size: 20px;
    }
</style>