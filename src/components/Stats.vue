<template>
  <div class="stats">
     <div class="left">
        <h1> A different component </h1>
        <p>There are currently {{countLinks}} links</p>
     </div>
     
  </div>
</template>

<script>

import {mapGetters} from 'vuex';
export default {
  name: 'Stats',
  computed: {
    ...mapGetters([
      'countLinks',
    ]),
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
