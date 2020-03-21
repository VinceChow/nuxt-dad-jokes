<template>
  <nuxt-link :to="`jokes/${joke.id}`">
    <div>
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
