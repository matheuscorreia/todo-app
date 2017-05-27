<template>
  <div id="app-wrapper">
    <main-pane v-bind:goals='goals'/>
    <secondary-pane v-bind:goals='goals'/>
  </div>
</template>

<script>
import PouchDB from 'pouchdb';
import uuid from 'uuid/v1';

import MainPane from './components/MainPane.vue';
import SecondaryPane from './components/SecondaryPane.vue';

export default {
  name: 'app',
  components: {
    'main-pane': MainPane,
    'secondary-pane': SecondaryPane
  },
  data: function () {
    return {
      goals: Array(0)
    }
  },
  beforeMount: function () {
    let db = new PouchDB('goals');
    let that = this;

    db.allDocs({include_docs: true}, function (err, response) {
      that.goals = response.rows.map(function (item) {
        return item.doc;
      });
    });
  }
}
</script>

<style scoped>
</style>
