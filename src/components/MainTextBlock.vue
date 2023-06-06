<template>
    <p class="vm-textBlock">
        <slot></slot>
    </p>
</template>

<script>
export default {
    name: "MainTextBlock",
}
</script>

<style lang="scss">
.vm-textBlock {
    color: $grey-dark;
    font-size: 12px;
    font-family: 'Roboto', sans-serif;

    @media only screen and (min-width: 762px) {
        font-size: 20px;
    }
}
</style>