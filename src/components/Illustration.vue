<template>
    <div class="illustration">
        <div class="illustration__img illustration__img-girl">
            <Image image="girl" />
        </div>
        <div class="illustration__img illustration__img-candy">
            <Image image="candy" />
        </div>
        <div class="illustration__img illustration__img-chip">
            <Image image="chip" />
        </div>
        <div class="illustration__img illustration__img-name">
            <Image image="name" />
        </div>
        <div class="illustration__img illustration__img-buble">
            <Image image="buble" />
        </div>
    </div>
</template>

<script setup>
import Image from "./Image.vue"
</script>

<style lang="scss">
.illustration {
    position: relative;
    display: inline-flex;
    min-height: rem(453);
    // flex-grow: 1;
    // height: 100%;
    flex: 1;
    width: 100%;
    background-image: url(@/assets/images/illustration.png);

    background-repeat: no-repeat;
    background-size: cover;
    background-position: center;
    
    // z-index: 1;
    &__img {
        position: absolute;
    }

    &__img-girl {
        bottom: 0;
        left: rem(38);
        width: rem(273);
        height: rem(297);
    }

    &__img-candy {
        bottom: rem(4.77);
        left: 0;
        width: rem(74.31);
        height: rem(64.65);
        transform: rotate(-8.779deg);
    }

    &__img-chip {
        top: rem(48);
        left: rem(-29);
        width: rem(77.47);
        height: rem(91.59);
        transform: rotate(-28.899deg);
    }

    &__img-name {
        top: rem(48);
        left: 50%;
        transform: translateX(-50%);
        width: rem(113);
        height: rem(56);
    }

    &__img-buble {
        top: rem(48);
        right: rem(-47.5);
        width: rem(138);
        height: rem(138);
        transform: rotate(-39.458deg);
    }
}

@include desc {
    .illustration {
        height: 100%;

        &__img-girl {
            left: rem(87);
            width: rem(610);
            height: rem(666);
        }

        &__img-candy {
            bottom: rem(321.49);
            // right: rem(859);
            left: rem(-173);
            width: rem(274);
            height: rem(274);
        }

        &__img-chip {
            top: rem(-54);
            // left: rem(-107);
            width: rem(251.831);
            height: rem(297.727);
        }

        &__img-name {
            top: rem(125);
            width: rem(217);
            height: rem(111);
        }

        &__img-buble {
            // top: rem(0.04);
            right: rem(-170.49);
            width: rem(545.247);
            height: rem(545.247);
        }
    }
}
</style>
