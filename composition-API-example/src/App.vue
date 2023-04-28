<script >
  import Cat from './components/Cat.vue'
  console.log(Cat)
  import { ref, reactive, computed, watch, watchEffect } from 'vue'

  export default {
    name: 'Home',
    setup() {
      const name = ref('Mario')  // by wrapping the setup variable in ref, allows the variable to be reactive
      const age = ref(30) 
      const names = ref(['mario', 'yoshi', 'luigi'])
      const search = ref('')
      const ninja = reactive({ name: 'Luigi', age: 35 })

      const updateRefExample = () => {
        name.value += '!'
      }

      const updateReactiveExample = () => {
        // .value is not needed
        // can NOT do primitive values IE strings, ints, basically non objects
        // ref can have less side effects
        ninja.age += 1
      }

      const matchingNames = computed(() => {
        return names.value.filter((name) => name.includes(search.value))
      })

      watch(search, () => {
        console.log('watch function ran')
      })

      watchEffect(() => {
        console.log('watchEffect function ran')
      })

      return { name, age, ninja, updateRefExample, updateReactiveExample, matchingNames, search, names }
    },
    components: {
      Cat
    }

    // non Composition API  way
    // data() {
    //   return {
    //     score: 5
    //   }
    // }

}
</script>



<template>
  <h1>Hello</h1>
  <h2>Ref Example</h2>
  <p ref="pTag">My name is {{ name }} and my age is {{ age }}</p>
  <button @click="updateRefExample">Click me</button>
  <button @click="age++">Add 1 to age</button>
  <input type="text" v-model="name">

  <br><br/>
  <h2>Reactive Example</h2>
  <p>{{  ninja.name }} - {{ ninja.age }}</p>
  <button @click="updateReactiveExample">Age {{ ninja.name}}</button>

  
  <br><br/>
  <h2>Computed Example</h2>
  <p>Search Term - {{ search }}</p>
  <input type="text" v-model="search">
  <div v-for="name in matchingNames" :key="name">{{ name }}</div>

  <Cat></Cat>
</template>