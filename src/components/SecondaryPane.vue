<template lang="html">
  <div id="secondary-pane-wrapper">
    <input v-model="goalName" type="text" name="goal-name" value="" />
    <button type="button" name="button" v-on:click="addGoal">Add</button>
  </div>
</template>

<script>
import PouchDB from 'pouchdb';

export default {
  props: ['goals'],
  data: function () {
    return {
      goalName: ""
    }
  },
  methods: {
    addGoal(){
      let db = new PouchDB('goals');
      let that = this;
      let newGoal = {
        _id: String(new Date().getTime()),
        name: this.goalName
      }
      db.put(newGoal)
      .then((err,response) => {
        this.goalName = "";
        this.goals.push(newGoal)
      }).catch();
    }
  }
}
</script>

<style lang="css">
</style>
