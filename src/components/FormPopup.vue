<template>
    <div class="form-popup">
        <div class="form-popup__container">
            <div class="form-popup__close">
                <Icon
                    iconName="close"
                    size="close"
                    @click="$emit('close-form')"
                />
            </div>
            <div class="form-popup__block">
                <FormIllustration />
                <Form />
            </div>
        </div>
    </div>
</template>

<script setup>
import FormIllustration from "./FormIllustration.vue"
import Form from "./Form.vue"
import Icon from "./Icon.vue"
</script>

<style lang="scss">
.form-popup {
    position: fixed;
    top: 0;
    left: 0;
    z-index: 100;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    padding: rem(28);
    overflow: scroll;

    &__close {
        position: absolute;
        top: rem(38);
        right: rem(38);
        z-index: 100;
        cursor: pointer;
    }
}

@include desc {
    .form-popup {
        width: rem(720);
        height: rem(704);

        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        padding: 0;
        overflow: hidden;
        border-radius: rem(16);

        &__container {
            height: 100%;
            width: 100%;
        }

        &__block {
            display: flex;
            align-items: center;
            height: 100%;
        }

        &__close {
            top: rem(16);
            right: rem(16);
        }
    }
}
</style>
