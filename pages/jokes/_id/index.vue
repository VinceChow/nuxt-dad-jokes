<template>
  <div>
    <nuxt-link to="/jokes">Back to Jokes</nuxt-link>
    <p>{{ joke && joke.joke }}</p>
  </div>
</template>

<script lang="ts">
import { Vue, Component } from 'vue-property-decorator';

interface IJoke {
  id: string;
  joke: string;
}

@Component
export default class SingleJoke extends Vue {
  private joke: IJoke | null = null;

  async created() {
    const config = {
      headers: {
        Accept: 'application/json'
      }
    };

    try {
      const res = await this.$axios.$get(
        `https://icanhazdadjoke.com/j/${this.$route.params.id}`,
        config
      );
      this.joke = res;
    } catch (err) {
      // eslint-disable-next-line no-console
      console.error(err);
    }
  }
}
</script>

<style scoped></style>
