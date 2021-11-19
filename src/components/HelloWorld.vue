<template>
  <div class="alert alert-info">
    <h2>{{ title }}</h2>
    <p ref="msg">{{ message }}</p>
  </div>
  <button class="btn btn-info" v-on:click="doAction">Click</button>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      title: 'HelloWorld',
      message: 'This is sample message.'
    }
  },
  mounted() {
      this.counter = 0;
  },
  methods: {
    doAction() {
      this.counter++;
      this.$refs.msg.innerHTML += '<h6>counted: ' + this.counter + '</h6>'
    }
  }
}
</script>
