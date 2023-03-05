<template>
  <div class="container">
    <h1>Random Baby Name Generator</h1>
    <p>Click the button to generate a random baby name.</p>
    <div class="options-container">
      <div class="option-container">
        <h4>1) Choose gender </h4>
        <div class="option-buttons">
          <button class="option">Man</button>
          <button class="option">Unisex</button>
          <button class="option">Girl</button>
        </div>
      </div>
      <div class="option-container">
        <h4>2) Choose the name popularity</h4>
        <div class="option-buttons">
          <button class="option">Trendy</button>
          <button class="option">Unique</button>
        </div>
      </div>
      <div class="option-container">
        <h4>3) Choose the name length</h4>
        <div class="option-buttons">
          <button class="option">Long</button>
          <button class="option">All</button>
          <button class="option">Short</button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.container {
  font-family: Arial, Helvetica, sans-serif;
  color: rgb(27, 60, 138);
  max-width: 50rem;
  margin: 0 auto;
  text-align: center;
}

h1 {
  font-size: 3rem;
}

.options-container {
  background-color: rgb(255, 238, 236);
  border-radius: 2rem;
  padding: 1rem;
  width: 95%;
  margin: 0 auto;
  margin-top: 4rem;
  position: relative;
}

.option {
  background-color: rgb(255, 238, 236);
  color: rgb(27, 60, 138);
  border: 1px solid rgb(27, 60, 138);
  border-radius: 6.5rem;
  padding: 0.75rem 2rem;
  font-size: 1rem;
  margin: 0.5rem;
  cursor: pointer;
}
</style>