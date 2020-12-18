<template>
    <div class="page-two">
        <h2>Page Two</h2>
        <p>{{ data.message }}</p>
    </div>
</template>

<script>
export default {
    name: 'PageTwo',
    props: {
        data: Object,
    },
}
</script>
