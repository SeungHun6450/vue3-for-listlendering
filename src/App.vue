<template>
<button
  @click="handler">
  Click me!
</button>
  <ul>
    <!-- <li
      v-for="(f, i) in fruits"
      :key="f">
      {{ f }}-{{ i + 1 }} -->
    <li
      v-for="{id, name} in newFruits"
      :key="id">
      {{ name }} - {{id}}
    </li>
  </ul>
</template>

<script>
// https://v3.ko.vuejs.org/guide/list.html#%E1%84%89%E1%85%A1%E1%86%BC%E1%84%90%E1%85%A2-%E1%84%8B%E1%85%B2%E1%84%8C%E1%85%B5
// 각 id를 고유하게 해주는 package, shortid 설치 후 import
import shortid from 'shortid'

export default {
  data() {
    return {
     fruits: ['Apple', 'Banana', 'Cherry']
    //  newFruits : [
    //    {id: 0, name: 'Apple'},
    //    {id: 1, name: 'Banana'},
    //    {id: 2, name: 'Cherry'}
    //  ]
    }
  },
  computed: {
    newFruits() {
      // return this.fruits.map((fruit, index) => {
      //   return {
      //     id: index,
      //     id: shortid.generate(),
      //     name: fruit
      //   }
      // })

      // shortid 사용 시, 간소화 작업
      return this.fruits.map(fruit => ({
        id: shortid.generate(),
        name: fruit
      }))
    }
  },
  methods: {
    handler() {
      this.fruits.push('Orange')
    }
  }
}
</script>