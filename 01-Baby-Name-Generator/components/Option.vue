<template>
  <div class="option-container">
    <h2>{{ props.option.title }}</h2>
    <div class="option-buttons">
      <button
        v-for="value in props.option.buttons"
        :key="value"
        class="option"
        :class="options[props.option.category] === value && 'option-active'"
        @click="options[props.option.category] = value">
        {{ value }}
      </button>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { Gender, Length, Popularity } from '@/data';

interface OptionProps {
  option: {
    title: string;
    category: string;
    buttons: Gender[] | Popularity[] | Length[];
  };
  options: {
    gender: Gender;
    popularity: Popularity;
    length: Length;
  };
}

const props = defineProps<OptionProps>();
</script>

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
