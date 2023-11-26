<template>
    <div class="main-content">
        <h1 class="main-content__title">
            Deposit 500, Get 500 USDT
            <span class="main-content__title-yellow"> AS A GIFT </span>
        </h1>
        <h2 class="main-content__subtitle">100% Cashback FOR VIPS Only</h2>
    </div>
</template>

<script></script>

<style lang="scss">
.main-content {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 24px;
    text-align: center;
    font-family: "GothamPro", sans-serif;
    text-transform: uppercase;

    &__title {
        font-weight: 400;
        color: $white;
        font-size: rem(24);
        line-height: rem(27.5);

        &-yellow {
            color: $yellow;
            font-weight: 700;
        }
    }

    &__subtitle {
        color: $white;
        font-size: rem(16);
        line-height: rem(26);
        color: $gray;
        font-weight: 400;
    }
}

@include desc {
    .main-content {
        display: flex;
        flex-direction: column;
        align-items: start;
        gap: 54px;
        text-align: left;
        width: rem(544);

        &__title {
            font-size: rem(60);
            line-height: rem(72);
        }

        &__subtitle {
        font-size: rem(24);
        line-height: rem(32);
    }
    }
}
</style>
