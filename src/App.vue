<template>
  <div id="app">
    <div class="container">
      <h1>TODO List Vue!</h1>
      <form @submit.prevent="add()">
        <input 
          type="text"
          class="input"
          v-model="newToDo"        
        />
      </form>
      <a class="waves-effect waves-light btn"  v-on:click="add()">ADD</a>
      <ol>
        <li v-for="(todo, i) in existingToDo">
          <strong>{{ todo.text }}</strong>
          <a class="waves-effect waves-light red darken-4 btn-small" @click="deleteToDo(i)">Remove</a>
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
ol {
  line-height: 50px;
}
</style>
