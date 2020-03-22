<template>
  <div class="flex justify-center h-screen">
    <div class="mx-auto">
      <div class="py-2">
        <nuxt-link
          class="shadow-sm bg-green-500 hover:bg-green-400 focus:shadow-outline focus:outline-none text-white font-bold py-2 px-2 rounded-lg"
          to="/jokes"
          >Back to Jokes</nuxt-link
        >
      </div>
      <div class="py-2">
        <div class="max-w-lg bg-white rounded-lg shadow-lg overflow-hidden">
          <div class="h-64 flex">
            <img class="flex-grow" :src="gifUrl" />
          </div>
          <div class="h-16 p-6 flex flex-wrap content-center">
            <p>{{ joke && joke.joke }}</p>
          </div>
        </div>
      </div>
    </div>
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
  private gifUrl: string = '';

  async created() {
    const config = {
      headers: {
        Accept: 'application/json'
      }
    };

    try {
      const jokeRes = await this.$axios.$get(
        `https://icanhazdadjoke.com/j/${this.$route.params.id}`,
        config
      );
      const gifRes = await this.$axios.$get(
        `https://api.giphy.com/v1/gifs/random?api_key=sXpGFDGZs0Dv1mmNFvYaGUvYwKX0PWIh&tag=laugh`
      );
      this.joke = jokeRes;
      this.gifUrl = gifRes.data.image_original_url;
    } catch (err) {
      // eslint-disable-next-line no-console
      console.error(err);
    }
  }
}
</script>

<style scoped></style>
