<template>
    <div class="card">
        <div class="card-header">
            <h2>{{ dataDate }}</h2>
            <h2 id="card-title">VueJs Tutorial Todo List</h2>
            <h2>{{addition}} tâches</h2>
        </div>
        <div class="card-content">
            <new-todo @counter=count></new-todo>
        </div>
    </div>
</template>

<script>
import newTodo from './new-todo.vue';
    export default {
  components: { newTodo },
        name: 'TodoList',
        props: {
            msg: String
        },
        data () {
            return{
                tasks : [],
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
                console.log(b)
                this.addition=b
            }
        }
    }
</script>

<style>
.card {
    background-color: white !important;
    border-radius: 10px;
    font-family: Roboto;
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
    display: flex;
    justify-content: center;

}
</style>