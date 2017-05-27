<template>
  <div id="main-pane-wrapper">
    <goal-card
    v-for="(goal, index) in goals"
    v-bind:goal="goal"
    v-bind:index="index"
    v-bind:key="index"
    />
  </div>
</template>

<script>
import GoalCard from './GoalCard.vue';

export default {
  props: ['goals'],
  name: 'main-pane',
  components: {
    'goal-card': GoalCard
  }
}
</script>

<style scoped>

</style>
