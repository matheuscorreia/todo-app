<template lang="html">
  <div class="goal-card-wrapper">
    <h1>
      {{goal.name}} - {{ index }}
    </h1>
    <button type="button" name="delete">Delete</button>
    <button type="button" name="edit">Edit</button>
  </div>
</template>

<script>
export default {
  props: ['goal', 'index']
}
</script>

<style lang="css" scoped>
</style>
