<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    Animal:
    <select v-model="selected">
      <option v-for="obj in objList" v-bind:value="obj">{{obj.description}}</option>
    </select>
    <div>
      Weight: <input v-model="weight" >
      <select v-model="weightUnit">
         <option>Lbs</option>
         <option>Kg</option>
      </select>
    </div>
    <div>
      Length/Height: <input v-model="length" >
      <select v-model="lengthUnit">
               <option>Feet</option>
               <option>Inches</option>
               <option>Meters</option>
               <option>Centimetres</option>
            </select>
    </div>
    <div>
      Wingspan: {{wingspan}}
    </div>
    <div>

       <img :src="imageLink" height="150" style="opacity: 0.5" />
    </div>
  </div>
</template>

<script>
const AnimalList = [
  {
    description: 'pig',
    weight: 169000,
    length: 1965
  }, {
    description: 'horse',
    weight: 563500,
    length: 2500
  }, {
    description: 'human',
    weight: 88677,
    length: 1770
  }
]

export default {
  name: 'hello',
  data () {
    return {
      msg: 'Flying pig wingspan calculator',
      weight: AnimalList[0].weight,
      length: AnimalList[0].length,
      objList: AnimalList,
      selected: AnimalList[0],
      weightUnit: 'Lbs',
      lengthUnit: 'Feet'
    }
  },
  computed: {
    wingspan: function () {
      return this.weight * this.length
    },
    imageLink: function () {
      return 'static/' + this.selected.description + '.png'
    }
  },
  watch: {
    selected: function (val) {
      this.weight = val.weight
      this.length = val.length
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
