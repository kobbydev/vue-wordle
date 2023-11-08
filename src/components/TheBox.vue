<script setup></script>

<template>
    <div>
        a
    </div>
</template>

<style scoped lang="scss">
div {
    text-transform: capitalize;
    /* padding: 10px; */
    border: 1px solid #333;
    width: 40px;
    aspect-ratio: 1;
    display: flex;
    justify-content: center;
    align-items: center;

    @media screen and (min-width: 768px) {
        div {
            width: 60px
        }
    }
}
</style>