<template>
  <div>
    <h1>About</h1>
    <p>This is about page.</p>
    <a
      href="https://github.com/vincent0813/nuxt-dad-jokes"
      target="_blank"
      class="bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-4 rounded"
    >
      Source Code
    </a>
  </div>
</template>

<script lang="ts">
import { Vue, Component } from 'vue-property-decorator';

@Component({
  head() {
    return {
      title: 'About Us',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Best place for corny dad jokes'
        }
      ]
    };
  }
})
export default class About extends Vue {}
</script>

<style scoped></style>
