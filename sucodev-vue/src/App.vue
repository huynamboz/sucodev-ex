<script setup>
import { ref } from 'vue'

const sum =  ref(0)
console.log(sum.value)

function calculate() {
  console.log(Number(a.value) + 1, Number(b.value), Number(c.value))
  const A = Number(a.value)
  const B = Number(b.value)
  const C = Number(c.value)
  const Y = Number(y.value)

  if (A === 0) { //ax^2 + bx + c = y
    if (B === 0) {
      sum.value = 'VN'
      return
    }
    sum.value = (Y - C) / B
  } else {
    let delta = B*B - (4 * A * C)

    if (delta < 0) {
      sum.value = 'VN'
    } else if (delta === 0) {
      const x = - B / (2*A)
      sum.value = `x1 = x2: ${x}`
    } else {
      const x1 = (-B + Math.sqrt(delta)) / (2 * A)
      const x2 = (-B - Math.sqrt(delta)) / (2 * A)
      sum.value = `x1: ${x1}, x2: ${x2}`
    }
  }
}

const rawHTML = ref(`
  <h1 style="color: red;">Hello world</h1>
`)

// 2 way binding - two way binding
// prefix
const a = ref(0)
const b = ref(0)
const c = ref(0)
const y = ref(0)
</script>
<template>
 
  
  <input type="text" v-model="a"> <br>
  <input type="text" v-model="b"> <br>
  <input type="text" v-model="c"> <br>
  <input type="text" v-model="y"> <br>
  <button @click="calculate">Submit {{ sum }}</button>
  result ax^2 + bx + c: {{ sum }}
</template>