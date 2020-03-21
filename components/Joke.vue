<template>
  <nuxt-link :to="`jokes/${joke.id}`">
    <div
      class="mx-10 my-5 bg-white hover:bg-gray-100 rounded-lg shadow-lg p-4 flex flex-col justify-between leading-normal"
    >
      <p>{{ joke.joke }}</p>
    </div>
  </nuxt-link>
</template>

<script lang="ts">
import { Vue, Component, Prop } from 'vue-property-decorator';

interface IJoke {
  id: string;
  joke: string;
}

@Component
export default class Joke extends Vue {
  @Prop({ type: Object, required: true }) readonly joke!: IJoke;
}
</script>

<style scoped></style>
