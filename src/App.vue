<script setup>
import { ref } from "vue";

const showModel = ref(false);

</script>

<template>
  <h1>Keep track of import memos</h1>
  <header>
    <div v-if="showModel" class="add_modal_screen">
      <div class="modal">
        <p class="leadText">Add a memo:</p>
        <input placeholder="Title" />
        <textarea
          name="memos"
          id="memos"
          cols="30"
          rows="10"
          placeholder="What is your memo?"
        ></textarea>
        <button class="modal_button">Add Memo</button>
        <button @click="showModel = false" class="modal_close">close</button>
      </div>
    </div>
    <h4 class="leadText">Add a new memo</h4>
    <button @click="showModel = true">+</button>
  </header>

  <main>
    <p class="your_memos">Memos:</p>
    <div class="card-container">
      <div class="card">
        <p class="date">04/34/20002</p>
        <p class="memoTitle">Title</p>
        <p class="main-text">
          Lorem ipsum dolor sit amet consectetur, adipisicing elit. Ipsum culpa
          ab id dolorum inventore! Blanditiis culpa necessitatibus earum iure
          similique!
        </p>
        <button>Delete</button>
      </div>
    </div>
  </main>
</template>

<style scoped>
.add_modal_screen {
  position: absolute;
  width: 100vw;
  height: 100vh;
  background-color: rgba(24, 24, 24, 0.8);
  z-index: 400;
  display: flex;
  align-items: center;
}

button {
  display: flex;
  text-align: center;
  justify-content: center;
  border: 0px;
  color: black;
  background-color: coral;
  width: 100px;
  height: 30px;
  margin: 25px;
  border-radius: 10px;
  font-size: 20px;
}
.card {
  width: 300px;
  height: 300px;
  border: 3px;
  border-color: coral;
  /* box-shadow: ; */
  padding: 20px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  margin-right: 20px;
  margin-bottom: 20px;
}
.card-container {
  display: flex;
  width: 100%;
  grid-template-columns: 50px 1fr;
}
.date {
  font-size: small;
  font-weight: bold;
  padding-bottom: 20px;
  color: #4f9c7a;
}

/* header {
   line-height: 3.0; 
} */

.leadText {
  font-weight: bold;
  font-size: 25px;
  color: coral;
}
.memoTitle {
  color: coral;
  font-weight: bold;
  padding-bottom: 10px;
}
.modal {
  width: 700px;
  border-radius: 10px;
  background-color: #535353;
  border: #4f9c7a;
  border-style: solid;
  position: inherit;
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
