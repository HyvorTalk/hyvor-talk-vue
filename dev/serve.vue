<script>
import { defineComponent } from 'vue';
// Uncomment import and local "components" registration if library is not registered globally.
//import { Embed } from  '@/entry.esm';
//import { CommentCount } from  '@/entry.esm';

export default defineComponent({
  name: 'ServeDev',
  components: {
  //  Embed
  //CommentCount
  }
});
</script>

<template>
  <div id="app">
    <Embed website-id='3257' id="14"></Embed>
  </div>
</template>
