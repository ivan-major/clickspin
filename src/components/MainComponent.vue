<template>
    <div :class="isOpenForm ? 'main main__disabled' : 'main'">
        <MainInfo @open-from="onOpenFrom" />
        <Illustration />
    </div>

    <FormPopup v-if="isOpenForm" @close-form="onCloseFrom" />
</template>

<script setup>
import { ref } from "vue"
import MainInfo from "./MainInfo.vue"
import Illustration from "./Illustration.vue"
import FormPopup from "./FormPopup.vue"

const isOpenForm = ref(false)

const onOpenFrom = () => {
    isOpenForm.value = true
}

const onCloseFrom = () => {
    isOpenForm.value = false
}
</script>

<style lang="scss">
.main {
    overflow: hidden;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;

    &__disabled {
        pointer-events: none;
        max-height: 100vh;
        overflow: hidden;
        &::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            z-index: 100;
            width: 100%;
            height: 100%;

            background: rgba(0, 0, 0, 0.7);
    
            backdrop-filter: blur(7.5px);
        }
    }
}

@include desc {
    .main {
        flex-direction: row;
        height: 100vh;
        // min-height: none;
    }
}
</style>
