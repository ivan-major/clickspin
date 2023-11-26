<template>
    <div :class="`img img__${props.image}`" />
</template>

<script setup>
const props = defineProps({
    image: {
        type: String,
        default: "",
    },
})
</script>

<style lang="scss">
.img {
    display: inline-flex;
    height: 100%;
    width: 100%;

    background-repeat: no-repeat;
    background-size: cover;
    background-position: center;
    z-index: 1;

    &__diamond {
        background-image: url(@/assets/images/diamond.png);
    }

    &__brilliant {
        background-image: url(@/assets/images/brilliant.png);
    }

    &__light {
        background-image: url(@/assets/images/light.svg);
    }

    &__buble {
        background-image: url(@/assets/images/buble.png);
    }

    &__candy {
        background-image: url(@/assets/images/candy.png);
    }

    &__chip {
        background-image: url(@/assets/images/chip.png);
    }

    &__girl {
        background-image: url(@/assets/images/girl.png);
    }

    &__name {
        background-image: url(@/assets/images/name.png);
    }

    &__lights-forms {
        background-image: url(@/assets/images/lights-forms.png);
        background-position: top;
    }
}
</style>
