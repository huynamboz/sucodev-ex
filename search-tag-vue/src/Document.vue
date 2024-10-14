<script setup>
import { ref } from 'vue';

const languages = ref(
  [
    "html",
    "css",
    "javascript",
    "php"
  ]
)

// languages.forEach((item, index) => {
  
// });

const notifications = ref([
  {
    message: "Notice 1",
    hide: true,
  },
  {
    message: "Notice 2",
    hide: false
  },
  {
    message: "Notice 3",
    hide: false
  }
])

const person = ref({
  name: "hinam",
  birthday: "1/1/1111"
})

const isEnable = ref(true)
</script>
<template>
  <div>
    <ul>
      <li v-for="(item) in languages">
        {{ item }} - 
        <!-- {{ index * 100 }} -->
      </li>
    </ul>

    <p>notifications</p>

    <!-- destructuring -->
    <button v-for="noti in notifications">
      <p v-if="noti.hide === false">{{ noti.message }}</p>
    </button>
    <br>
    
    <template v-for="noti in notifications">
      <button v-if="noti.hide === false">
        <p>{{ noti.message }}</p>
      </button>
    </template>

    <!-- loop through object -->
     <div>
      <p>Name: {{ person.name }}</p>
      <ul>
        <li v-for="(val, key, index) in person">
          {{ key }} : {{ val }} - {{ index }}
        </li>
      </ul>
     </div>

     <button v-for="n in 10">
      button - {{ n }}
     </button>

     <!-- fragment -->
      <template v-for="n in 10">
        <button>asd</button>
        <div>{{ n }}</div>
        <input type="text">
      </template>


      <button v-if="isEnable === true">SUBMIT</button>
      <p v-else-if="isEnable = false">button submit disabled</p>
      <p v-else></p>
      <button @click="isEnable = !isEnable">Disable submit {{ isEnable }}</button>
  </div>
</template>