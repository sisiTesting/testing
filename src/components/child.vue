/* eslint-disable */

<template>
  <div>
    <div>
        <input v-model="inputField" />
        <button @click="submitData"> Submit </button>
    </div>

    <div v-if="data.child && data.child.length > 0">
      <div v-for="kid in data.child" v-bind:key="kid.key">
        <ul> <li> <child :data="kid" /> </li> </ul>
      </div>
    </div>

  </div>
</template>

<script>
import { EventBus } from './eventBus.js';

export default {
  name: 'child',
  props: {
    data: [Array, Object],
  },
  data: function() {
    return {
      inputField: "",
    }
  },
  created: function() {
    if(this.data && this.data.key) {
      this.inputField = this.data.key;
    }
  },
  methods: {
    submitData: function () {
      console.log("aaaaa i have been clicked with new data", this.inputField);
      EventBus.$emit("child--submitData", this.inputField)
    },
  },
};

</script>
