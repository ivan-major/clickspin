<template>
    <section class="main-info">
        <div class="main-info__block">
            <LogoComponent />

            <div class="main-info__container">
                <MainTitleComponent />
                <RegistrationButton @open-from="onOpenForm"/>
            </div>
        </div>

        <div class="image image__diamond">
            <Image image="diamond" />
        </div>

        <div class="image image__brilliant">
            <Image image="brilliant" />
        </div>

        <div class="image image__light-1">
            <Image image="light" />
        </div>

        <div class="image image__light-2">
            <Image image="light" />
        </div>
    </section>
</template>

<script setup>
import LogoComponent from "./LogoComponent.vue"
import MainTitleComponent from "./MainTitleComponent.vue"
import RegistrationButton from "./RegistrationButton.vue"

import Image from "./Image.vue"

const emit = defineEmits(["open-from"])

const onOpenForm = () => {
    emit("open-from")
}
</script>

<style lang="scss">
.main-info {
    position: relative;
    padding-top: rem(56);
    // display: flex;
    // flex-direction: column;
    // align-items: center;
    // gap: 24px;
    // justify-content: center;
    min-height: rem(453);
    flex: 1;
    // height: 50%;
    // flex-grow: 1;
    width: 100%;
    background-color: $main-color;
    overflow: hidden;

    &__block {
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 24px;
    }

    &__container {
        padding: 0 16px;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        gap: 48px;
        text-align: center;
    }
}

.image {
    position: absolute;

    &__diamond {
        bottom: rem(3.81);
        left: rem(4.25);
        width: rem(116);
        height: rem(116);
    }

    &__brilliant {
        bottom: rem(11.79);
        right: rem(20.85);
        width: rem(67);
        height: rem(67);
    }

    &__light-1 {
        bottom: rem(49);
        right: rem(-11);
        width: rem(84);
        height: rem(84);
    }

    &__light-2 {
        top: rem(38);
        right: rem(-11);
        width: rem(75);
        height: rem(45);
        transform: rotate(-21.748deg);
    }
}

@include desc {
    .main-info {
        height: 100%;
        padding: 0;

        &__block {
            position: absolute;
            top: rem(148);
            left: rem(222);
            align-items: start;
            gap: 54px;
        }

        &__container {
        padding: 0;
        align-items: start;
        // justify-content: start;
        gap: 101px;
        text-align: start;
    }
    }

    .image {
        &__diamond {
            bottom: rem(373.18);
            left: rem(-107);
            width: rem(312);
            height: rem(312);
        }

        &__brilliant {
            bottom: rem(49.79);
            right: rem(221.79);
            width: rem(131.989);
            height: rem(131.989);
        }

        &__light-1 {
            bottom: rem(114);
            right: rem(106.58);
            width: rem(237.418);
            height: rem(142.451);
        }

        &__light-2 {
            top: rem(79.21);
            right: rem(47.41);
            width: rem(212.336);
            height: rem(127.527);
        }
    }
}
</style>
