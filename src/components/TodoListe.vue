<template>
<div class="allTask">
    <div v-for="task in tasks" :key="task" class="task">
        <input type="checkbox" @click="made(task)" class="checkboxTask"/>
            <p v-bind:class="{checked: task.isMade}">{{ task.content }}</p>
        <button @click="remove(task)" class="removeButton"><i class="fa fa-trash" aria-hidden="true"></i></button>
    </div>
</div>
</template>

<script>

export default {
  name: 'TodoListe',
  props: ['tasks'],
  methods: {
      made(task){
          this.$emit('made', task)
      },
      remove(task){
          this.$emit('remove', task)
      }
  }
}
</script>

<style>
    .allTask{
        padding: 0 40px;
    }
    .task{
        display: flex;
        justify-content: space-between;
        margin: 40px 0;
    }
    .checked{
        text-decoration: line-through;
    }
    .checkboxTask{
        border-radius: 25px;
        transform: scale(3);
    }
    .removeButton{
        background-color: red;
        border: none;
        border-radius: 25px;
        padding: 10px 13px;
        color:white;
    }
</style>