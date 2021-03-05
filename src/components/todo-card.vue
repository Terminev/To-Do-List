<template>
    <div class="card">
        <div class="card-header">
            <h2>{{ dataDate }}</h2>
            <h2 id="card-title">VueJs Tutorial Todo List</h2>
            <h2>{{ addition }} tâches</h2>
        </div>
        <div class="card-content">
            <new-todo @counter=count @sendTask='Add' ></new-todo>
            <todo-list :task="task" @endtask='End' @deletetask ='Del' @deleteall ='DelA'></todo-list>
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
        data () {
            return{
                task : [],
                addition : 0,
            }
        },
        computed: {
            dataDate: function(){
                var date = new Date();
                let days = ["Dimanche", "Lundi", "Mardi", "Mercredi", "Jeudi", "Vendredi", "Samedi"]
                let months = ["Janvier", "Fevrier", "Mars", "Avril", "Mai", "Juin", "Juillet", "Aout", "Septembre", "Octobre", "Novembre", "Decembre"]
            
                var dayNumber = date.getDate();
                var actualDay = days[date.getDay()]
                var actualMonth = months[date.getMonth()]

                return actualDay + " " + dayNumber + " " + actualMonth + " "
            }
        },
        methods : {
            count(b){
                this.addition=b
            },
            End(c) {
                if(this.task[c].checked === false){
                    this.task[c].checked = true
                }else{
                    this.task[c].checked = false

                }
            },
            Del(d) {
                this.task.splice(d, 1)
                this.addition--
            },
            DelA(f) {
                this.task.splice(f)
                this.addition =0
            },
            Add(e) {
                
                this.task.push({description: e, checked:false})
                console.log(e)
            }
        }
    }
</script>

<style>
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
</style>