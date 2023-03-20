<script setup>
import { ref, watch, onMounted, computed } from "vue";
import Nav from "../components/nav.vue";

const showModel = ref(false);
const newMemo = ref("");
const newTitle = ref("");
const memos = ref([]);

const memoAsc = computed(() => memos.value.sort((a, b) =>{
  return b.title - a.title
}))

// setting memo arry into local storage

watch(memos, (newVal) => {
  localStorage.setItem('memos', JSON.stringify(newVal))
}, {deep: true})

onMounted( () => {
  memos.value = JSON.parse(localStorage.getItem('memos')) || []
})


const addMemo = () => {
  memos.value.push({
    id: Math.floor(Math.random() * 100),
    input: newTitle.value,
    text: newMemo.value,
    date: new Date().toLocaleDateString("en-US"),
 });
 showModel.value = false;
 newMemo.value = ""
 newTitle.value = ""
 
}

//removing a memo

const removeMemo = memo  => {
  memos.value = memos.value.filter(m => m !== memo)

}
</script>

<template>
  <!-- <Nav /> -->
  <h2>Keep track of import memos</h2>
  <header>
    <div v-if="showModel" class="add_modal_screen">
      <div class="modal">
        <p class="leadText">Add a memo:</p>
        <input v-model="newTitle" placeholder="Title" />
        <textarea
          name="memos"
          id="memos"
          cols="30"
          rows="10"
          placeholder="What is your memo?"
          v-model="newMemo"
        ></textarea>
        <button @click="addMemo()" class="modal_button">Add Memo</button>
        <button @click="showModel = false" class="modal_close">close</button>
      </div>
    </div>
    <h4 class="leadText">Add a new memo</h4>
    <button @click="showModel = true">+</button>
  </header>
  <main>
    <p class="your_memos">Memos:</p>
    <div class="card-container">
      <div v-for="memo in memos" class="card">
        <p class="date">{{ memo.date }}</p>
        <p class="memo_title">Title: {{ memo.input }}</p>
        <p class="main_text">Memo:
          {{ memo.text }}</p>
        <button @click="removeMemo(memo)" class="del_button">Done</button>
  
      </div>
    </div>
  </main>
</template>

<style scoped>
.add_modal_screen {
  position: absolute;
  width: 100vw;
  height: 100vh;
  background-color: #181818cc;
  z-index: 400;
  display: flex;
  align-items: center;
}

button {
  display: flex;
  text-align: center;
  justify-content: center;
  position: bottom;
  border: 0px;
  color: black;
  background-color: coral;
  width: 100px;
  height: 30px;
  margin: 25px;
  border-radius: 10px;
  font-size: 20px;
  cursor: pointer;
}
.card {
  width: 200px;
  height: 300px;
  border: 3px;
  border-color: coral;
  border-style: solid;
  border-width: 0.5px;
  padding: 10px;
  display: flex;
  flex-direction: column;
  margin-right: 20px;
  margin-bottom: 20px;
}
.card-container {
  display: flex;
  width: 100%;
  grid-template-columns: 10px 1fr;
  margin-top: 20px;
}
.date {
  font-size: small;
  font-weight: bold;
  padding-bottom: 10px;
  color: #4f9c7a;
  text-align: center;
}
.del_button {
  position: inherit;
  display: flex;
  justify-items: end;
  justify-content: baseline;

}
/* header {
   line-height: 3.0; 
} */

.leadText {
  font-weight: bold;
  font-size: 25px;
  color: #ff7f50;
}
.memo_title {
  color: coral;
  font-weight: bold;
  padding-bottom: 10px;
}
.modal {
  width: 900px;
  height: 500px;
  border-radius: 10px;
  background-color: #535353;
  border: #4f9c7a;
  border-style: solid;
  position: relative;
  display: flex;
  flex-direction: column;
}
.modal_button {
  width: 100%;
  position: relative;
  margin: 20px 0px 0px 0px;
}
.modal_close {
  width: 100%;
  position: relative;
  margin: 20px 0px 0px 0px;
  background-color: #4f9c7a;
  border-radius: none;
}
textarea {
  padding: auto;
}
.your_memos {
  font-weight: bold;
  font-size: 25px;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }
  header .leadTezt {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
