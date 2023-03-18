<script setup lang="ts">
import { Gender, Length, Popularity, names } from '@/data';

interface OptionsState {
  gender: Gender;
  popularity: Popularity;
  length: Length;
}

const options = reactive<OptionsState>({
  gender: Gender.GIRL,
  popularity: Popularity.TRENDY,
  length: Length.ALL,
}); // reactive для хранения состояния объекта

const selectedNames = ref<string[]>([]); // ref для хранения состояния массива

const computeSelectedNames = () => {
  const filteredNames = names
    .filter((name) => name.gender === options.gender)
    .filter((name) => name.popularity === options.popularity)
    .filter((name) => {
      if (options.length === Length.ALL) return true;
      else return name.length === options.length;
    });

  selectedNames.value = filteredNames.map((name) => name.name);
};

const optionsArray = [
  {
    title: '1) Choose a gender',
    category: 'gender',
    buttons: [Gender.GIRL, Gender.UNISEX, Gender.BOY],
  },
  {
    title: '2) Choose the name popularity',
    category: 'popularity',
    buttons: [Popularity.TRENDY, Popularity.UNIQUE],
  },
  {
    title: '3) Choose the name length',
    category: 'length',
    buttons: [Length.LONG, Length.ALL, Length.SHORT],
  },
];
</script>

<template>
  <div class="container">
    <h1>Random Baby Name Generator</h1>
    <p>Click the button to generate a random baby name.</p>
    <div class="options-container">
      <Option
        v-for="option in optionsArray"
        :key="option.title"
        :option="option"
        :options="options" />
    </div>
    <button class="primary" @click="computeSelectedNames">Generate Name</button>
  </div>
  <div class="cards-container">
    <div v-for="name in selectedNames" key="name" class="card">
      <h4>{{ name }}</h4>
      <p>x</p>
    </div>
  </div>
</template>

<style scoped>
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

.primary {
  background-color: rgb(27, 60, 138);
  color: rgb(255, 238, 236);
  border-radius: 6.5rem;
  border: none;
  padding: 0.75rem 4rem;
  font-size: 1rem;
  margin-top: 1rem;
  cursor: pointer;
}

.cards-container {
  display: flex;
  margin-top: 3rem;
  flex-wrap: wrap;
}

.card {
  background-color: rgb(255, 238, 236);
  border-radius: 2rem;
  padding: 0.1rem;
  width: 28%;
  margin: 0 auto;
  margin-top: 1rem;
  position: relative;
}

.card p {
  position: absolute;
  top: 0;
  left: 92.5%;
  cursor: pointer;
  color: black;
}
</style>
