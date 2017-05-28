<template lang="html">
  <div id="secondary-pane-wrapper" class="col s4">
    <h5 class="center-align pane-title">Type here</h5>
    <textarea id="textarea1" class="materialize-textarea" v-model="goalName" data-length="120"></textarea>
    <a class="waves-effect waves-light btn center-align" v-on:click="addGoal">Add</a>
  </div>
</template>

<script>
import PouchDB from 'pouchdb';

export default {
  props: ['goals', 'updateList'],
  data: function () {
    return {
      goalName: ""
    }
  },
  methods: {
    addGoal(){
      let db = new PouchDB('goals');
      let newGoal = {
        _id: String(new Date().getTime()),
        name: this.goalName
      }
      db.put(newGoal)
      .then((err,response) => {
        this.goalName = "";
        this.updateList();
      }).catch();
    }
  }
}
</script>

<style lang="css" scoped>
#secondary-pane-wrapper{
  background-color: #9EEBEE;
  height: 100%;
  position: fixed;
  right: 0px;
  box-shadow: 0 4px 5px 0 rgba(0,0,0,.14), 0 1px 10px 0 rgba(0,0,0,.12), 0 2px 4px -1px rgba(0,0,0,.2);
}

.pane-title{
  font-weight: 100;
}
</style>
