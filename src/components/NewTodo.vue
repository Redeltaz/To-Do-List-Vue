<template>
    <div class="addTask">
        <input type="text" placeholder="Nouvelle tâche..." v-model="taskContent" class="inputContent"/>
        <button class="add" @click="addTask()">+</button>
    </div>
</template>

<script>

export default {
  name: 'new-todo',
  data () {
    return {
      taskContent: ''
    }
  },
  methods: {
      addTask(){
          if(this.taskContent != ''){
                this.$emit('newTask', this.taskContent)
                this.taskContent = ''
          }
      }
  }
}
</script>
<style>
    .addTask{
        display:flex;
        justify-content:center;
        margin: 20px 0;
    }

    .addTask input {
        border: none;
        border-bottom: 1px solid #00d0b2;
    }

    .addTask button{
        margin-left: 20px;
        width: 40px;
        height: 40px;
        background-color: #00d0b2;
        border: none;
        border-radius: 25px;
        color: white;
    }
</style>