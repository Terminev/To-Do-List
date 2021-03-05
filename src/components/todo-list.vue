<template>
    <div>
        <ul>
            <li class="nametasks" v-for="(task, index) in task" :key="(task, index)">
                <input type="checkbox" v-on:click='check(index)'>
                <h3 v-bind:class="{'end':task.checked}">{{ task.description}}</h3>
                <i class="fas fa-trash" v-on:click="addition +=-1;remover(index)"></i>
            </li>
        </ul>
        <button class="CtaDel" v-on:click="deleteAll">Vider les Tâches</button>
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
        color: red;
    }

    .nametasks {
        display: flex;
        align-items: center;
        width: 80%;
        justify-content: space-evenly;
        margin: 0 auto;
        margin-top: 25px;
    }
    .CtaDel {
        margin-top: 25px;
    }
</style>