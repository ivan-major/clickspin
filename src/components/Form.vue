<template>
    <div class="form">
        <form action="" class="form__container">
            <div class="form__title">Registration</div>
            <div class="item item-email">
                <div
                    :class="`item__content item__content-label ${
                        isInFocus.email ? 'item__content_active-label' : ''
                    }`"
                >
                    {{ form.email.label }}
                </div>

                <input
                    name="email"
                    v-model="form.email.value"
                    type="email"
                    :class="`form__input form__input-email ${
                        !isValidInput.email ? 'form__input-error' : ''
                    }`"
                    :placeholder="form.email.placeholder"
                    @focus="onFocusInput($event)"
                    @blur="onBlurInput($event)"
                />

                <div
                    v-if="!isValidInput.email"
                    class="item__content item__content-error"
                >
                    Provide a valid e-mail address
                </div>
            </div>

            <div class="item item-password">
                <div
                    :class="`item__content item__content-label ${
                        isInFocus.password ? 'item__content_active-label' : ''
                    }`"
                >
                    {{ form.password.label }}
                </div>

                <input
                    name="password"
                    v-model="form.password.value"
                    type="password"
                    :class="`form__input form__input-password ${
                        !isValidInput.password ? 'form__input-error' : ''
                    }`"
                    :placeholder="form.password.placeholder"
                    @focus="onFocusInput($event)"
                    @blur="onBlurInput($event)"
                />

                <div
                    v-if="!isValidInput.password"
                    class="item__content item__content-error"
                >
                    Provide a valid password
                </div>
            </div>

            <div class="conditions">
                <input
                    v-model="form.conditions.value"
                    type="checkbox"
                    name="conditions"
                    id="conditions"
                    class="conditions__input"
                />
                <label for="conditions" class="conditions__label">
                    By checking this box when registering on this site, the user
                    confirms that he is over 18 years of age and has read,
                    understood and accepted the
                    <a href="/" target="_blank" class="conditions__link"
                        >Terms and Conditions.</a
                    >
                </label>
            </div>

            <button
                :class="`form__button ${
                    isValidForm
                        ? 'form__button-active'
                        : 'form__button-disabled'
                }`"
                :disabled="!isValidForm"
                @click="onSubmit($event)"
            >
                <div class="button__text">Create an account</div>
            </button>

            <div class="form__register-with register-with">
                <div class="register-with__text">Or register with:</div>
                <div class="register-with__icons">
                    <div
                        v-for="method in registrationMethod"
                        class="register-with__icon"
                    >
                        <Icon :iconName="method.icon" />
                    </div>
                </div>
            </div>
        </form>
    </div>
</template>

<script setup>
import { reactive, ref, computed, watch } from "vue"
import Icon from "./Icon.vue"

const form = reactive({
    email: {
        value: "",
        placeholder: "Email",
        label: "Email",
    },
    password: {
        value: "",
        placeholder: "Password",
        label: "Password",
    },
    conditions: {
        value: false,
    },
})

const registrationMethod = ref([
    {
        name: "metamask",
        icon: "metamask",
    },
    {
        name: "apple",
        icon: "apple",
    },
    {
        name: "facebook",
        icon: "facebook",
    },
    {
        name: "google",
        icon: "google",
    },
])

const isInFocus = ref({
    email: false,
    password: false,
})

const isValidInput = ref({
    email: true,
    password: true,
})

const isValidForm = computed(() => {
    return (
        isValidInput.value.email &&
        isValidInput.value.password &&
        form.conditions.value &&
        form.email.value &&
        form.password.value
    )
})

const onFocusInput = (event) => {
    switch (event.target.name) {
        case "email":
            isInFocus.value.email = true
            form.email.placeholder = ""
            break
        case "password":
            isInFocus.value.password = true
            form.password.placeholder = ""
            break
    }
}

const onBlurInput = (event) => {
    switch (event.target.name) {
        case "email":
            if (form.email.value === "") {
                isInFocus.value.email = false
                form.email.placeholder = "Email"
            }

            isValidInput.value.email = emailValidator(form.email.value)
            break
        case "password":
            if (form.password.value === "") {
                isInFocus.value.password = false
                form.password.placeholder = "Password"
            }

            isValidInput.value.password = passwordValidator(form.password.value)
            break
    }
}

const emailValidator = (value) => {
    return !value
        ? true
        : /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|.(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/.test(
              value
          )
}

const passwordValidator = (value) => {
    return !value ? true : value.length >= 6
}

const onSubmit = (event) => {
    event.preventDefault()
    if (!isValidForm.value) return

    const body = {
        email: form.email.value,
        password: form.password.value,
    }

    console.log(body)
}

</script>

<style lang="scss">
.form {
    background-color: $form-background-color;
    position: relative;
    padding: rem(16);

    &__container {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        gap: 32px;
        text-align: center;
        margin: rem(16) 0;
    }

    &__title {
        color: $input-text-color;
        text-align: center;
        font-family: "Stolzl", sans-serif;
        font-size: rem(20);
        font-style: normal;
        font-weight: 400;
        line-height: rem(24);
        letter-spacing: rem(0.4);
    }

    &__input {
        width: 100%;
        padding: rem(16) rem(16) rem(16) rem(40);
        border-radius: rem(8);
        background: $form-background-color;
        color: #ffffff;
        font-family: "Stolzl", sans-serif;
        font-size: rem(14);
        border: 1px solid #353535;
        font-weight: 400;
        line-height: rem(16);
        letter-spacing: rem(0.28);
        background-repeat: no-repeat;
        background-position: rem(16) 50%;

        &::placeholder {
            color: $input-placeholder-color;
        }

        &:focus {
            outline: none;
            border-radius: 8px;
            border: 1px solid $input-placeholder-color;
            box-shadow: 0px 0px 6px 0px rgba(252, 252, 252, 0.32);
        }

        &:-webkit-autofill {
            -webkit-box-shadow: inset 0 0 0 50px $form-background-color !important;
            -webkit-text-fill-color: $input-text-color !important;
        }

        &-password {
            background-image: url(@/assets/icons/bxs_lock.svg);
        }

        &-error {
            border: 1px solid $form-error-color;

            &:focus {
                border: 1px solid $form-error-color;
            }
        }
    }

    .item {
        position: relative;
        width: 100%;

        &__content {
            color: $input-placeholder-color;
            font-family: "Stolzl", sans-serif;
            font-size: rem(10);
            font-style: normal;
            font-weight: 400;
            line-height: rem(16);
            letter-spacing: rem(0.2);
            background-color: $form-background-color;
            // display: none;
            // opacity: 0;
            z-index: -1;

            &-label {
                position: absolute;
                top: 50%;
                transform: translateY(-50%);
                left: rem(40);
            }

            &_active-label {
                top: rem(-8);
                transform: none;
                left: rem(16);
                // opacity: 1;
                z-index: 1;
                // display: block;
                transition: all 1s ease;
            }

            &-error {
                position: absolute;
                bottom: rem(-8);
                right: rem(16);
                color: $form-error-color;
                z-index: 1;
            }
        }

        &::before {
            content: "";
            display: block;
            position: absolute;
            top: 50%;
            left: rem(16);
            transform: translateY(-50%);
            width: rem(16);
            height: rem(16);
        }

        &-email {
            &::before {
                background-image: url(@/assets/icons/email.svg) !important;
            }
        }

        &-password {
            &::before {
                background-image: url(@/assets/icons/bxs_lock.svg);
            }
        }
    }

    .conditions {
        display: flex;
        align-items: start;
        justify-content: start;
        gap: 8px;

        &__label {
            position: relative;
            padding: 0 0 rem(18) rem(26);

            font-family: "Stolzl", sans-serif;
            font-size: rem(10);
            font-style: normal;
            font-weight: 400;
            line-height: rem(14);
            letter-spacing: rem(0.2);
            text-align: left;
            color: $input-placeholder-color;
        }

        &__link {
            color: $yellow;
            text-decoration: none;
        }

        &__input {
            position: absolute;
            z-index: -1;
            opacity: 0;
        }

        &__input + label::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            display: inline-block;
            width: rem(18);
            height: rem(18);
            flex-shrink: 0;
            flex-grow: 0;
            border: 1px solid $input-placeholder-color;
            border-radius: rem(2);
            // margin-right: 0.5em;
            // background-repeat: no-repeat;
            // background-position: center center;
            // background-size: 50% 50%;
        }

        &__input:checked + label::before {
            background-image: url(@/assets/icons/checked.svg);
            border: none;
        }

        // &__input {
        //     width: rem(16);
        //     height: rem(16);
        //     border: 1px solid $input-text-color;
        //     // background-color: $yellow;
        //     border-radius: rem(2);
        //     outline: none;
        //     cursor: pointer;

        //     &:checked {
        //         background-color: $yellow;
        //         border: 1px solid $yellow;
        //     }
        // }
    }

    &__button {
        width: 100%;
        padding: rem(16);
        text-align: center;

        font-family: "Stolzl", sans-serif;
        font-size: rem(14);
        font-style: normal;
        font-weight: 400;
        line-height: rem(16);
        letter-spacing: rem(0.28);
        border-radius: rem(10);
        border: none;
        color: $button-disabled-text-color;
        cursor: pointer;

        &-disabled {
            background-color: $button-disabled-background-color;
        }

        &-active {
            background-color: $yellow;
            transition: background-color 1s ease;

            &:hover {
                background-color: $input-text-color;
                transition: background-color 1s ease;
            }
        }
    }

    .register-with {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        gap: 12px;

        &__text {
            font-family: "Stolzl", sans-serif;
            font-size: rem(12);
            font-style: normal;
            font-weight: 500;
            line-height: rem(16);
            letter-spacing: rem(0.36);
            text-align: center;
            color: $input-text-color;
        }

        &__icons {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
        }

        &__icon {
            width: rem(58);
            height: rem(48);
            border-radius: rem(8);
            background-color: $form-icon-background-color;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;

            &:hover {
                background-color: $gray;
            }
        }
    }
}

@include desc {
    .form {
        display: flex;
        justify-content: center;
        align-items: center;

        flex: 1;
        height: 100%;

        padding: 0;

        &__container {
            padding: 0 16px;
        }
    }
}
</style>
