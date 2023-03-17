<script setup>
</script>

<template>
  <h1>Keep track of your import memos</h1>

  
  <header>
    <h4 class='leadText'>Click to add memos</h4>
    <button class="addMemos">+</button>
  </header>

  <main>  
    <p class="your_memos">Memos:</p>
      <div class="card-container">
      <div class="card">
        <p class="date">04/34/20002</p>
        <p class="memoTitle">Title</p>
        <p class="main-text">Lorem ipsum dolor sit amet consectetur, adipisicing elit. Ipsum culpa ab id dolorum inventore! Blanditiis culpa necessitatibus earum iure similique!</p>
        <button>Delete</button>
      </div>
    </div>
  </main>
</template>

<style scoped>
header {
  /* line-height: 3.0; */
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
.memoTitle {
  color:coral;
  font-weight: bold;
  padding-bottom: 10px
}
.leadText {
  font-weight: bold;
  font-size: 25px;
  color:coral;
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
