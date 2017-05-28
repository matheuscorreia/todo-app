<template>
  <div id="main-pane-wrapper" class="col s8">
    <h1 class="pane-title center-align">To do</h1>
    <goal-card
    v-for="goal in goals"
    v-bind:goal="goal"
    v-bind:key="goal.id"
    v-on:delete="deleteGoal"
    />
  </div>
</template>

<script>
import GoalCard from './GoalCard.vue';

export default {
  props: ['goals', 'updateList'],
  name: 'main-pane',
  components: {
    'goal-card': GoalCard
  },
  methods: {
    deleteGoal(goal){
      let db = new PouchDB('goals');
      db.remove(goal).then(() => {this.updateList()});
    }
  }
}
</script>

<style scoped>
#main-pane-wrapper{
  background-color: #ededed;
  height: auto;
  min-height: 100%;
  position: absolute;
  left: 0px;
}

.pane-title{
  font-weight: 100;
}
</style>
