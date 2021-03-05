<template>

    <div class="card">
        <div class="cardHeader">
            <p>{{getDate()}}</p>
            <p>VueJs Tutorial ToDo List</p>
            <p>{{tasks.length}}</p>
        </div>
        <NewTodo @newTask="addTask" />
        <TodoListe :tasks="tasks" @made="changeCheck" @remove="removeTask" />
    </div>

</template>

<script>
import NewTodo from '@/components/NewTodo.vue'
import TodoListe from '@/components/TodoListe.vue'

export default {
  name: 'TodoCard',
  components: {
    NewTodo,
    TodoListe
  },
  data () {
    return {
      tasks: []
    }
  },
  methods: {
      getDate(){
            let date = new Date()

            let days = ['Dimanche', 'Lundi', 'Mardi', 'Mercredi', 'Jeudi', 'Vendredi', 'Samedi']
            let months = ['Janvier', 'Février', 'Mars', 'Avril', 'Mai', 'Juin', 'Juillet', 'Août', 'Septembre', 'Octobre', 'Novembre', 'Décembre']
            let day = days[date.getDay()]
            let month = (1 + date.getMonth())
            let number = date.getDate().toString()
            return `${day} ${number} ${months[month]}`
      },
      addTask(content){
            let newTask = {
                content: content,
                isMade: false
            }
            this.tasks.push(newTask)
      },

      changeCheck(task){
          if(task.isMade){
              task.isMade = false
          }else{
              task.isMade = true
          }
          console.log(task)
      },

      removeTask(task){
          let actualTask = this.tasks.indexOf(task)
          this.tasks.splice(actualTask, 1)
      }
  },
}
</script>

<style>
    .card{
        background-color: white;
        width: 70%;
        border-radius: 15px;
    }

    .cardHeader{
        display: flex;
        justify-content: space-between;
        padding: 20px 80px;
        border-bottom: 1px solid rgba(0, 0, 0, 0.2)
    }

    .cardHeader p:nth-child(2){
        color: #00d0b2;
    }
</style>