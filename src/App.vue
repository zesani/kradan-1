<template lang="html">
  <div class="">
    <div class="directory">
      <item  class="item" :model="treeData"></item>
    </div>
    <div class="atom">
        <!-- Menu -->
      <ul class="menu">
        <li class="">
          <div class="fileName">index.html</div>
          <div class="close-icon"></div>
        </li>
        <li class="">
          <div class="fileName">index.html</div>
          <div class="close-icon"></div>
        </li>
      </ul>
        <!-- code -->
      <article class="code">
        <ol class="lines">
          <li v-for="(code,index) in codes"><pre>{{index+1}}&nbsp&nbsp&nbsp&nbsp&nbsp<code v-html="highlight(code)"></code></pre></li>
        </ol>
      </article>
      </div>
    </div>
  </div>
</template>

<script>
var data = {
  name: 'My Tree',
  children: [
    {
      name: 'hello',
      text: 'var = 20'
    },
    {
      name: 'wat',
      text: 'var t = 15'
    },
    {
      name: 'D1',
      children: [
        {
          name: 't1'
        },
        {
          name: 't2'
        }
      ]
    }
  ]
}
import hljs from 'highlight.js'
import Item from './components/Item'
export default {
  data () {
    return {
      treeData: data,
      codes: [
        `import hljs from 'highlight.js'`,
        `export default {`,
        `  data () {`,
        `    return {`,
        `      code: []`,
        `    }`,
        `  },`,
        `  computed: {},`,
        `  mounted () {},`,
        `  methods: {`,
        `    highlight: function (value) {`,
        `      if (value !== undefined) {`,
        `        return hljs.highlightAuto(value).value`,
        `      }`,
        `    }`,
        `  },`,
        `  components: {}`,
        `}`,
        `import hljs from 'highlight.js'`,
        `export default {`,
        `  data () {`,
        `    return {`,
        `      code: []`,
        `    }`,
        `  },`
      ]
    }
  },
  computed: {},
  mounted () {},
  methods: {
    highlight: function (value) {
      if (value !== undefined) {
        return hljs.highlightAuto(value).value
      }
    }
  },
  components: {
    Item
  }
}
</script>
<style lang="css">
@import url("../node_modules/highlight.js/styles/atom-one-dark.css");
/* The colors Duke, the colors! */
.directory {
  background-color: #21252b;
  height: 100%;
  position: absolute;
  left: 0%;
  right: 90%;
  color: #abb2bf;
  overflow: auto;
  border-right: #0a0b12 1px solid;
  padding-top: 50px;
  padding-left: 15px;
}
.atom {
  background-color: #282c34;
  position: absolute;
  left: 10%;
  right: 0px;
  height: 100%;
  color: #abb2bf;
}
* {
  box-sizing: border-box; }
*,
body {
  background-color: #24282f;
  margin: 0;
  padding: 0;
  overflow: hidden;
}

ul li {
  list-style: none;
}
.code {
  font-family: "Cousine", monospace;
  font-size: 1.1em;
  line-height: 1.35em;
  font-weight: normal;
  cursor: text;
  height: 100%;
}
.lines li {
  counter-increment: item;
  padding-left: 4em;
  margin-left: -4em;
  border-left-width: 2px;
  border-left-style: solid;
  border-left-color: transparent;
}
  .lines li div:first-child {
    padding-right: 1em;
  }

.lines li:before {
  content: counter(item) " ";
  padding: 0 1em;
  text-align: right;
  display: block;
  float: left;
  margin-left: -4em;
  box-sizing: content-box;
  width: 1.25em;
}

ol.lines {
  counter-reset: item;
  list-style-type: none;
  width: 100%;
  border-left-width: 1em;
  border-left-color: transparent;
  border-left-style: solid;
  padding-top: 1em;
  padding-bottom: 1em;
  height: 100%;
  overflow: auto;
}

.menu {
  background-color: #21252b;
  display: flex;
  height: 3em;
  padding-top: 7px;
}
  .menu li {
    /*flex: 1;*/
    min-width: 7em;
    height: 3em;
    line-height: 3em;
    padding: 0;
    margin: 0;
    text-align: center;
    display: inline-block;
    background-color: #21252b;
    color: #666c77;
    cursor: default;
    border-bottom: solid #181a1f 1px; }
    .menu li .fileName {
      overflow: hidden;
      white-space: nowrap;
      text-overflow: ellipsis;
      text-overflow: clip;
      mask: linear-gradient(to left, transparent, #000000 1em) no-repeat;
      margin: 0 0em;
      width: 300px;
    }
    .menu li:not(:first-child) {
      border-left: solid #181a1f 1px;
    }
    .menu li.current {
      color: #d7dae0;
      background-color: #282c34;
      border-left: 2px #528bff solid;
      border-top: 1px #353840 solid;
      border-right: 1px #2c3038 solid;
      border-bottom: 1px #282c34 solid;
    }
</style>
