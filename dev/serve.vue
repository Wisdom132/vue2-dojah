<script>
import Vue from 'vue';
import Vue2Dojah from '@/vue2-dojah.vue';

export default Vue.extend({
  name: 'ServeDev',
  components: {
    Vue2Dojah
  }
});
</script>

<template>
  <div id="app">
    <Vue2Dojah />
  </div>
</template>
