<template lang="html">
    <div class="item">
      <div @click="toggle">
        <span v-if="isFolder">{{open ? 'v' : '>'}}</span>&nbsp&nbsp
        {{model.name}}
      </div>
      <ul v-show="open" v-if="isFolder">
        <item class="item" v-for="model in model.children" :model="model"></item>
      </ul>
    </div>
</template>

<script>
import Item from './Item'
export default {
  name: 'item',
  props: ['model'],
  data () {
    return {
      open: false
    }
  },
  component: {
    Item
  },
  computed: {
    isFolder: function () {
      return this.model.children
    }
  },
  methods: {
    toggle: function () {
      if (this.isFolder) {
        this.open = !this.open
      }
    }
  }
}
</script>

<style lang="css">
.folder {

}
body {
  font-family: Menlo, Consolas, monospace;
  color: #444;
}
.item {
  line-height: 2em;
  cursor: pointer;
}
.bold {
  font-weight: bold;
}
ul {
  padding-left: 1em;
  line-height: 1.5em;
  list-style-type: dot;
}
</style>
