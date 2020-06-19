<template>
  <div id="app">
    <div class="container">
      <h1>TODO Lsit Vue!</h1>
      <input 
        type="text"
        class="input"
        v-model="newToDo"
      />
      <button class="add-button" v-on:click="add()">ADD</button>
      <ol>
        <li v-for="(todo, i) in existingToDo">
          <span>
            {{ todo.text }}
          </span>
          <button class="delete-button" @click="deleteToDo(i)">X</button>
        </li>
      </ol>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      newToDo: '',
      existingToDo: [
        {
          text: 'Get Groceries',
          id: 0
        },
        {
          text: 'Walk Dog',
          id: 1
        }
      ]
    }
  },
  methods:{
    add(){
      if (this.newToDo === ""){
        return;
      }
      this.existingToDo.push({ 
         text: this.newToDo,
         id: new Date().valueOf()
      })
      this.newToDo = ''
    },
    deleteToDo(i){
      this.existingToDo.splice(i, 1)
    }
  }
}
</script>

<style>
</style>
