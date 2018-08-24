/* eslint-disable */

<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>
    <div v-for="(data, index) in allData"
         v-bind:key="index" >
      <child
        :data="data"
      />
    </div>
  </div>
</template>

<script>
import child from './child';
import { EventBus } from './eventBus.js';

export default {
  name: 'HelloWorld',
  components: {
    child,
  },
  data() {
    return {
      msg: 'Welcome to Your Vue.js App',
      allData: [{
        key: 'grandParent',
        child: [{
          key: 'parent',
          child: [{
            key: 'child',
            child: [{
              key: 'grandChild1',
              child: [],
            }, {
              key: 'grandchild2',
              child: [],
            }],
          }, {
            key: 'child2',
            child: [],
          }],
        }, {
          key: 'parent2',
          child: [{
            key: 'child3',
            child: [],
          }],
        }, {
          key: 'grandParent2',
          child: [{
            key: 'parent3',
            child: [],
          }],
        }],
      }, {
        key: 'sibling-grandparent',
        child: [],
      }, {
        key: 'sibling-grandparent',
        child: [],
      }, {
        key: 'sibling-grandparent',
        child: [],
      }],
    };
  },
  mounted: function() {
    EventBus.$on("child--submitData", this.getDataFromChild)
  },
  methods: {
    getDataFromChild: function(newData) {
      console.log("i am parent! gotta!", newData)
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
