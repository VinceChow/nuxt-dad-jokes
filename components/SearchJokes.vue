<template>
  <form @submit.prevent="onSubmit">
    <input v-model="text" type="text" placeholder="Search Jokes" />
    <input type="submit" value="Search" />
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
