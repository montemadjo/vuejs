<template>
  <div id="app">
    <h4 class="bg-primary text-white text-center p-2">
      {{name}}'s TO DO LIST...
    </h4>
    <div class="container-fluid p-4">
      <div class="row">
        <div class="col font-weight-bold">Task</div>
        <div class="col-2 font-weight-bold">Done</div>
      </div>
      <div class="row" v-for="t in filteredTasks" v-bind:key="t.action">
        <div class="col">{{t.action}}</div>
        <div class="col-2 text-center">
          <input type="checkbox" v-model="t.done" class="form-check-input"/> 
          {{t.done}}
        </div>
      </div>
      <div class="row bg-secondary py-2 mt-2 text-white">
        <div class="col text-center">
          <input type="checkbox" v-model="hideCompleted" class="form-check-input" />
          <label class="form-check-label font-weight-bold">
            Hide completed Tasks
          </label>

        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data(){
    return {
      name: "Bogdan",
      tasks: [
        {action: "Buy Flowers", done: false},
        {action: "Get Shoes", done: false},
        {action: "Collect Tickets", done: true},
        {action: "Call Ypie", done: false}
      ],
      hideCompleted: true
    }
  },
  computed: {
    filteredTasks(){
      return this.hideCompleted ? this.tasks.filter(t => !t.done) : this.tasks
    }
  }
}
</script>