<template>
    <div>
        <h1 class="vm-heading">
            <slot></slot>
        </h1>
    </div>
</template>

<script>
export default {
    name: "MainHeading",
}
</script>

<style lang="scss">
.vm-heading {
    font-family: "Montserrat", sans-serif;
    font-size: 32px;
    font-weight: bold;
    line-height: 150%;
    color: $black;
    display: inline-block;

    @media only screen and (min-width: 762px) {
        font-size: 62px;
    }
}
</style>