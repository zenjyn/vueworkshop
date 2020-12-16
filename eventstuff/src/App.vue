<template>
  <h1>Event Stuff</h1>
  <CounterDisplay :count="this.count" />
  <CounterControl @delta="delta" :amount="7" />
  <CounterControl @delta="delta" :amount="-3" />
</template>

<script>
import CounterDisplay from '@/components/CounterDisplay.vue';
import CounterControl from '@/components/CounterControl.vue';

export default {
  name: 'App',
  components: {
    CounterDisplay,
    CounterControl,
  },
  data() {
    return {
      count: 0,
    }
  },
  methods: {
    delta(amount) {
      this.count += amount;
    },
  }
}
</script>

<style>
</style>
