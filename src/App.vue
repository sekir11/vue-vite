<template>

  <img alt="Vue logo" src="./assets/logo.png" />
  <div id="app">
    <HelloWorld />
    <Calc :title="message" v-on:result-event="appAction" />
    <div class="mt-3 text-left">
      <table class="table" v-html="log"></table>
    </div>
    <div>
      <button class="btn btn-danger" v-on:click="doClear">Clear Log</button>
    </div>
  </div>
</template>

<script>
import Calc from './components/Calc.vue'
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    Calc, HelloWorld
  },
  data() {
    return {
      message: 'CALC',
      result: []
    }
  },
  computed: {
    log() {
      let table = '<tr><th>Expression</th><th>Value</th></tr>';
      if (this.result.length > 0) {
        for(var i in this.result) {
          table += '<tr><td>' + this.result[i][0] + '</td><th>' + this.result[i][1] + '</th></tr>'        
          }
      }
      return table;
    }
  },
  methods: {
    appAction(exp, res) {
      this.result.unshift([exp, res]);
      var log = JSON.stringify(this.result);
      localStorage.setItem('log', log);
    },
    doClear() {
      if (confirm('ログを全て削除します。')) {
        localStorage.removeItem('log');
        this.result = [];
      }
    }
  }
}
</script>
