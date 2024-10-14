<script setup>
import { ref } from 'vue';

const languages = ref(['html', 'css', 'javascript'])

const data = ref('')

function handleEnter() {
  languages.value.push(data.value)
  data.value = ''
}

function handleDelete(index) {
  languages.value.splice(index, 1)
}
</script>
<template>
  <div class="container">

    <button>Click me</button>
    <!-- popup -->
     <div class="popup-container">
      <div class="popup-main">
        <div class="popup-header">
          <span class="popup-close__btn">x</span>
        </div>

        <div class="popup-content">
          Are you sure you want to delete this item?
        </div>
        <div class="popup-action">
          <button>Cancel</button>
          <button>Confirm</button>
        </div>
      </div>
     </div>

    <div class="list">

      <!-- item -->
      <div class="item" v-for="(language, index) in languages">
        <p>{{ language }}</p>
        <svg @click="handleDelete(index)" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"><path fill="currentColor" d="M19 6.41L17.59 5L12 10.59L6.41 5L5 6.41L10.59 12L5 17.59L6.41 19L12 13.41L17.59 19L19 17.59L13.41 12z"/></svg>
      </div>
      <input type="text" v-model="data" @keyup.enter="handleEnter">

    </div>
  </div>
</template>
<style scoped>
/* popup */
.popup-container {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: #7a7a7a;
  display: flex;
  justify-content: center;
  align-items: center;
}
.popup-main {
  background-color: #fff;
  padding: 20px;
  border-radius: 12px;
  display: grid;
  gap: 20px;
}

.popup-header {
  display: flex;
  justify-content: flex-end;
}

.popup-action {
  display: flex;
  gap: 12px;
}

.popup-action button {
  flex: 1;
}
.container {
  padding: 20px;
}

.list {
  border: 1px solid #7a7a7a;
  padding: 10px;
  border-radius: 6px;
  margin-top: 10px;
  display: flex;
  gap: 6px;
  flex-wrap: wrap;
}

.item {
  display: flex;
  align-items: center;
  background-color: #b5b5b5;
  width: fit-content;
  padding: 4px;
  border-radius: 4px;
}
</style>