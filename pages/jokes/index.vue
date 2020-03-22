<template>
  <div class="items-center justify-center">
    <SearchJokes @search-text="searchText" />
    <Joke v-for="joke in jokes" :key="joke.id" :joke="joke" />
  </div>
</template>

<script lang="ts">
import { Vue, Component } from 'vue-property-decorator';
import Joke from '~/components/Joke.vue';
import SearchJokes from '~/components/SearchJokes.vue';

interface IJoke {
  id: string;
  joke: string;
}

@Component({
  head() {
    return {
      title: 'All the Jokes',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Best place for corny dad jokes'
        }
      ]
    };
  },
  components: { Joke, SearchJokes }
})
export default class Jokes extends Vue {
  private jokes: IJoke[] = [];

  async created() {
    const config = {
      headers: {
        Accept: 'application/json'
      }
    };

    try {
      const res = await this.$axios.$get(
        'https://icanhazdadjoke.com/search',
        config
      );
      this.jokes = res.results;
    } catch (err) {
      // eslint-disable-next-line no-console
      console.error(err);
    }
  }

  async searchText(text: string) {
    const config = {
      headers: {
        Accept: 'application/json'
      }
    };

    try {
      const res = await this.$axios.$get(
        `https://icanhazdadjoke.com/search?term=${text}`,
        config
      );
      this.jokes = res.results;
    } catch (err) {
      // eslint-disable-next-line no-console
      console.error(err);
    }
  }
}
</script>

<style scoped></style>
