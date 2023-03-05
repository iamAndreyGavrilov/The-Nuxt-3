<script setup lang="ts">

enum Gender {
  GIRL = 'Girl',
  BOY = 'Boy',
  UNISEX = 'Unisex',
}

enum Popularity {
  TRENDY = 'Trendy',
  UNIQUE = 'Unique',
}

enum Length {
  LONG = 'Long',
  ALL = 'All',
  SHORT = 'Short',
}


interface OptionsState {
  gender: Gender;
  popularity: Popularity;
  length: Length;
}

const option = reactive<OptionsState>({
  gender: Gender.GIRL,
  popularity: Popularity.TRENDY,
  length: Length.ALL,
}) // reactive для хранения состояния объекта
</script>

<template>
  <div class="container">
    <h1>Random Baby Name Generator</h1>
    <p>Click the button to generate a random baby name.</p>
    <div class="options-container">
      <div class="option-container">
        <h4>1) Choose gender </h4>
        <div class="option-buttons">
          <button class="option"
                  :class="option.gender === Gender.BOY && 'option-active'"
                  @click="option.gender = Gender.BOY">Boy
          </button>
          <button class="option" :class="option.gender === Gender.UNISEX && 'option-active'"
                  @click="option.gender = Gender.UNISEX">Unisex
          </button>
          <button class="option" :class="option.gender === Gender.GIRL && 'option-active'"
                  @click="option.gender = Gender.GIRL">Girl
          </button>
        </div>
      </div>
      <div class="option-container">
        <h4>2) Choose the name popularity</h4>
        <div class="option-buttons">
          <button class="option" :class="option.popularity === Popularity.TRENDY && 'option-active'"
                  @click="option.popularity = Popularity.TRENDY">Trendy
          </button>
          <button class="option" :class="option.popularity === Popularity.UNIQUE && 'option-active'"
                  @click="option.popularity = Popularity.UNIQUE">Unique
          </button>
        </div>
      </div>
      <div class="option-container">
        <h4>3) Choose the name length</h4>
        <div class="option-buttons">
          <button class="option" :class="option.length === Length.LONG && 'option-active'"
                  @click="option.length = Length.LONG">Long
          </button>
          <button class="option" :class="option.length === Length.ALL && 'option-active'"
                  @click="option.length = Length.ALL">All
          </button>
          <button class="option" :class="option.length === Length.SHORT && 'option-active'"
                  @click="option.length = Length.SHORT">Short
          </button>
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

.option-active {
  background-color: rgb(27, 60, 138);
  color: rgb(255, 238, 236);
}
</style>