<template>
  <div>
    <h1>About</h1>
    <p>This is about page.</p>
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
