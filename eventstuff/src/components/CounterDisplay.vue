<template>
  <p>{{ count }}</p>
</template>

<script>
export default {
  name: 'CounterValue',
  props: {
    count: Number,
  },
};
</script>

