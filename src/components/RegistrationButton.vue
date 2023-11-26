<template>
    <button class="registration-button" @click="onOpenFrom">
        <span class="registration-button__text">Become a vip-player</span>
    </button>
</template>

<script setup>
const emit = defineEmits(["open-from"])

const onOpenFrom = () => {
    emit("open-from")
}
</script>

<style lang="scss">
.registration-button {
    padding: rem(17) rem(56);
    display: flex;
    align-items: center;
    justify-content: center;
    width: fit-content;
    background-color: $yellow;
    border-radius: rem(29);
    border: none;
    outline: none;
    cursor: pointer;

    &__text {
        font-family: "GothamPro", sans-serif;
        font-size: rem(14);
        line-height: rem(24);
        color: $main-color;
        font-weight: 700;
        text-transform: uppercase;
    }

    &:hover {
        background-color: $input-text-color;
        transition: all 0.5s ease;
    }
}

@include desc {
    .registration-button {
        &__text {
            font-size: rem(20);
            line-height: rem(24);
        }
        transition: background-color 1s ease;

        &:hover {
            background-color: $input-text-color;
            transition: background-color 1s ease;
        }
    }
}
</style>
