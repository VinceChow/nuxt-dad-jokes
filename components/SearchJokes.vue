<template>
  <form class="w-full max-w-sm py-5" @submit.prevent="onSubmit">
    <div class="md:flex md:items-center mb-6">
      <div class="md:w-2/3 px-5">
        <input
          id="inline-full-name"
          v-model="text"
          class="bg-white-200 appearance-none rounded-lg shadow-sm w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none border-white focus:bg-white focus:border-green-500"
          type="text"
          placeholder="Joke"
        />
      </div>
      <div class="md:w-1/3">
        <button
          class="shadow-sm bg-green-500 hover:bg-green-400 focus:shadow-outline focus:outline-none text-white font-bold py-2 px-2 rounded-lg"
          type="submit"
        >
          Search
        </button>
      </div>
    </div>
  </form>
</template>

<script lang="ts">
import { Vue, Component, Emit } from 'vue-property-decorator';

@Component
export default class SearchJokes extends Vue {
  private text: string = '';

  @Emit('search-text')
  onSubmit() {
    const temp = this.text;
    this.text = '';
    return temp;
  }
}
</script>

<style scoped></style>
