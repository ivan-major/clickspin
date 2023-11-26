<template>
    <div class="form-illustration">
        <div class="form-illustration__block">
            <div class="form-illustration__logo">
                <Icon iconName="logo" size="form" />

                <Icon iconName="clickspin" size="clickspin-form" />
            </div>

            <div class="form-illustration__info illustration-info">
                <div class="illustration-info__text">
                    Deposit 500,<br />
                    get 500 USDT as a gift
                </div>

                <div
                    class="illustration-info__text illustration-info__text-yellow"
                >
                    100% cashback for VIPs only
                </div>
            </div>
        </div>

        <div class="form-illustration__images">
            <div class="picture picture__img-lights-forms">
                <Image image="lights-forms" />
            </div>

            <div class="picture picture__img-girl">
                <Image image="girl" />
            </div>

            <div class="picture picture__img-candy-1">
                <Image image="candy" />
            </div>

            <div class="picture picture__img-candy-2">
                <Image image="candy" />
            </div>

            <div class="picture picture__img-buble">
                <Image image="buble" />
            </div>
        </div>
    </div>
</template>

<script setup>
import Icon from "./Icon.vue"
import Image from "./Image.vue"
</script>

<style lang="scss">
.form-illustration {
    min-height: rem(318);
    background: linear-gradient(180deg, #130625 0%, #1b0929 100%);
    padding-top: rem(54);
    // display: flex;
    // flex-direction: column;
    // align-items: center;
    // justify-content: center;
    // gap: 17px;
    position: relative;
    overflow: hidden;

    &__logo {
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 9px;
    }

    &__block {
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 24px;
        flex: 1;
    }

    &__images {
        position: absolute;
        width: 100%;
        flex: 1;
        height: 50%;
        margin-top: rem(17);
    }
}

.illustration-info {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 8px;

    &__text {
        font-family: "Stolzl", sans-serif;
        font-weight: 400;
        font-size: rem(16);
        line-height: rem(16);
        color: $white;
        text-transform: uppercase;
        text-align: center;
        letter-spacing: rem(0.32);

        &-yellow {
            color: $yellow;
        }
    }
}

.picture {
    position: absolute;

    &__img-lights-forms {
        width: 100%;
        height: 100%;
        bottom: 0;
        left: 0;
    }

    &__img-girl {
        bottom: rem(-7);
        left: rem(67);
        width: rem(164);
        height: rem(166);
    }

    &__img-candy-1 {
        top: 0;
        left: rem(-26);
        width: rem(75.384);
        height: rem(65.58);
        transform: rotate(-8.779deg);
    }

    &__img-candy-2 {
        bottom: rem(-32);
        left: rem(-7);
        width: rem(93.728);
        height: rem(81.543);
        transform: rotate(-76deg);
    }

    &__img-buble {
        top: rem(0);
        right: rem(-32);
        width: rem(102.202);
        height: rem(102.202);
        transform: rotate(-48.343deg);
    }
}

@include desc {
    .form-illustration {
        width: 50%;
        height: 100%;
        flex: 1;

        &__images {
            height: 100%;
            bottom: 0;
            left: 0;
        }
    }

    .picture {
        &__img-lights-forms {
            height: 80%;
        }

        &__img-girl {
            bottom: 0;
            left: rem(8);
            width: rem(365);
            height: rem(399.006);
        }

        &__img-candy-1 {
            top: rem(299);
            left: rem(14);
            width: rem(75.892);
            height: rem(66.026px);
        }

        &__img-candy-2 {
            bottom: rem(-30);
            left: rem(-8);
            width: rem(105.691);
            height: rem(91.951);
            transform: rotate(-76deg);
        }

        &__img-buble {
            top: rem(212);
            right: rem(-32);
            width: rem(99.923);
            height: rem(99.923);
            transform: rotate(-48.343deg);
        }
    }
}
</style>
