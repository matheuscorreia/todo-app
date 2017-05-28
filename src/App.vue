<template>
    <div class="row">
      <main-pane
        v-bind:goals='goals'
        v-bind:updateList='updateList'
      />
      <secondary-pane
        v-bind:goals='goals'
        v-bind:updateList='updateList'
      />
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
    this.updateList();
  },
  methods: {
    updateList() {
      let db = new PouchDB('goals');
      db.allDocs({include_docs: true}, (err, response) => {
        this.goals = response.rows.map(function (item) {
          return item.doc;
        });
      });
    }
  }
}
</script>

<style>
.row{
  margin: 0;
}
</style>
