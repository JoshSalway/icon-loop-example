<template>
  <div class="hello">
    <ul id="v-for-object">
      <li v-for="(number, index) in 25" 
        v-bind:key="index"
        v-clipboard:copy="number"
        v-clipboard:success="onCopy"
        v-clipboard:error="onError"
      >
        <span v-if="showNumber" v-text="number" v-bind:key="index"></span>
        <span v-else>icon</span>
      </li>
    </ul>
  </div>
</template>

<script>
import _ from 'lodash';

export default {
  name: 'HelloWorld',
  data: function () {
    return {
      showNumber: true,
    }
  },
  methods: {
    onCopy: function (e) {
      console.log('You just copied: ' + e.text)
      this.showNumber = false
      console.log(this.selectItem)
      _.delay(() => {
        this.showNumber = true
      }, 2000);
    },
    onError: function () {
      console.log('Failed to copy texts')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 40px;
  font-size: 48px;
  cursor: pointer;
}
a {
  color: #42b983;
}
</style>
