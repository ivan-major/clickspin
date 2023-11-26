<template>
    <div class="logo">
        <Icon iconName="logo" size="logo" />
        <Icon iconName="clickspin" size="clickspin" />
    </div>
</template>

<script setup>
import Icon from './Icon.vue';
</script>

<style lang="scss">
.logo {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: rem(142);
}

@include desc {
    .logo {
        width: rem(235);
        align-items: end;
        gap:15px
    }
}
</style>