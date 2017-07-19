<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    Animal:
    <select v-model="selected">
      <option v-for="obj in objList" v-bind:value="obj">{{obj.description}}</option>
    </select>
    <div>
      Weight: <input v-model="weight" >
    </div>
    <div>
      Length/Height: <input v-model="length" >
    </div>
    <div>
      Wingspan: {{wingspan}}
    </div>
  </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      msg: 'Flying pig wingspan calculator',
      weight: 100,
      length: 30,
      objList: [{
        description: 'Pig'
      }, {
        description: 'Horse'
      }],
      selected: {
        description: 'Pig'
      }
    }
  },
  computed: {
    wingspan: function () {
      return this.weight * this.length
    }
  }
}
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
