<template>
    <div class="card">
        <div class="card-header">
            <h2>{{ dataDate }}</h2>
            <h2 id="card-title">VueJs Tutorial Todo List</h2>

            <h2 v-if="addition > 1">{{ addition }} tâches</h2>

            <h2 v-else>{{ addition }} tâche</h2>
        </div>
        <div class="card-content">
            <new-todo @sendTask='Add'></new-todo>
            <todo-list :task="task" @endtask='End' @deletetask='Del' @deleteall='DelA'></todo-list>
            <h3 class="nothing" v-if="addition == 0"> Aucune tâche</h3>
            <button class="CtaDel" v-if="addition > 1" v-on:click="deleteAll">Vider les Tâches</button>
        </div>
    </div>
</template>

<script>
    import newTodo from './new-todo.vue';
    import TodoList from './todo-list.vue';
    export default {
        components: {
            newTodo,
            TodoList,
        },
        name: 'TodoCard',
        props: {
            msg: String
        },
        data() {
            return {
                task: [],
                addition: 0,
            }
        },
        computed: {
            dataDate: function () {
                var date = new Date();
                let days = ["Dimanche", "Lundi", "Mardi", "Mercredi", "Jeudi", "Vendredi", "Samedi"]
                let months = ["Janvier", "Fevrier", "Mars", "Avril", "Mai", "Juin", "Juillet", "Aout", "Septembre",
                    "Octobre", "Novembre", "Decembre"
                ]

                var dayNumber = date.getDate();
                var actualDay = days[date.getDay()]
                var actualMonth = months[date.getMonth()]

                return actualDay + " " + dayNumber + " " + actualMonth + " "
            }
        },
        methods: {
            End(c) {
                if (this.task[c].checked === false) {
                    this.task[c].checked = true
                } else {
                    this.task[c].checked = false
                }
            },
            Del(d) {
                this.task.splice(d, 1)
                this.addition--
            },
            DelA(f) {
                this.task.splice(f)
                this.addition = 0
            },
            Add(e) {
                this.addition++
                this.task.push({
                    description: e,
                    checked: false
                })
                
            }
        }
    }
</script>

<style>
    .nothing {
        margin: 20px 0;
        width: 80;
        background-color: rgba(255, 0, 0, 0.164);
        border: none;
        padding-top: 50px;
        padding-bottom: 50px;
        font-size: 28px;
        color: black;
    }
    .card {
        background-color: white !important;
        border-radius: 10px;
    }

    .card-header {
        font-size: 22px;
        justify-content: space-between;
        padding: 15px;
        color: black;
    }

    #card-title {
        color: teal;
    }

    .card-content {
        display: block;
        justify-content: center;

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
</style>