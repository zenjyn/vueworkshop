<template>
  <button @click="delta">{{ this.label }}</button>
</template>

<script>
export default {
  name: 'IncButton',
  props: {
    amount: Number,
  },
  computed: {
    label() {
      return ((this.amount < 0) ? "Decrement" : "Increment") + ' ' + Math.abs(this.amount);
    },
  },
  methods: {
    delta() {
      this.$emit("delta", this.amount);
    },
  },
};
</script>

