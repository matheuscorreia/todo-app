<template lang="html">
  <div class="row">
    <div class="col s12">
      <div class="card white darken-1">
        <div class="card-content white-text">
          <span class="card-title" style="color:black">{{goal.name}}</span>
        </div>
        <div class="card-action">
          <a class="card-option" v-on:click="deleteGoal">Remove</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['goal'],
  methods: {
    deleteGoal() {
      this.$parent.deleteGoal(this.goal);
    }
  }
}
</script>

<style lang="css" scoped>
.card-wrap{
  width: 100%;
}
.card-option{
  cursor: pointer;
  color: #71adb0 !important;
  transition: color .3s ease;
}
.card-option:hover{
  color: #496a6c !important;
}
</style>
