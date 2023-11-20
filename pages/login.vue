<template>
    <div class="page">
        <div class="text-center">
            <NuxtLink to="/">
                <img src="@/assets/img/reglogo.svg" alt="">
            </NuxtLink>
        </div>

        <div class="form">
            <div class="form__body">
                <h1>Авторизация</h1>

                <div class="inputs">
                    <div>
                        <label for="email">электронная почта</label>
                        <input type="email" id="email" name="email" v-model="email">
                    </div>
                    <div>
                        <label for="password">пАРОЛЬ</label>
                        <img src="@/assets/img/eye.svg" alt="" @click="togglePasswordVisibility('password')" />
                        <input :type="showPassword ? 'text' : 'password'" id="password" name="password"
                            v-model="password" />
                    </div>
                </div>

                <div class="complete text-center">
                    <button @click="login">Войти</button>
                    <small class="error d-block">{{ error }}</small>
                    <span>Еще не с нами? <NuxtLink to="/register">Зарегистрироваться</NuxtLink> </span>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import global from '~/mixins/global';
import axios from 'axios';
export default {
    mixins: [global],
    data() {
        return {
            showPassword: false,
            showPasswordRepeat: false,
            pathUrl: 'https://mostshop.kz',
            email: '',
            password: '',
            error: '',
        }
    },
    methods: {
        login() {
            const path = `${this.pathUrl}/api/main/authorization`
            const csrf = this.getCSRFToken()

            axios.defaults.headers.common['X-CSRFToken'] = csrf;
            axios
                .post(path, { username: this.email, password: this.password })
                .then((res) => {



                    document.cookie = `Authorization=${res.data.token}; expires=Fri, 31 Dec 2023 23:59:59 GMT; path=/`;
                    localStorage.setItem('accountType', res.data.redirect_url)
                    if (res.data.redirect_url == 'buyer-account') {
                        window.location.href = '/'
                    }
                    if (res.data.redirect_url == 'seller-account') {
                        window.location.href = '/seller-account'
                    }


                    console.log(res)
                })
                .catch((error) => {
                    console.log(error);
                    this.error = error.response.data.non_field_errors.toString()
                });
        },
        togglePasswordVisibility(field) {
            if (field === 'password') {
                this.showPassword = !this.showPassword;
            } else if (field === 'password-repeat') {
                this.showPasswordRepeat = !this.showPasswordRepeat;
            }
        },
        togglePasswordVisibility(field) {
            if (field === 'password') {
                this.showPassword = !this.showPassword;
            } else if (field === 'password-repeat') {
                this.showPasswordRepeat = !this.showPasswordRepeat;
            }
        },
    },
    mounted() {
        const accType = localStorage.getItem('accountType')
        if (accType == 'buyer-account') {
            window.location.href = '/buyer-account'
        }
        else if (accType == 'seller-account') {
            window.location.href = '/seller-account'
        }
        else {
            console.log('not authorized')
        }
    }
}
</script>
<script setup>
useSeoMeta({
    title: 'Авторизация | Most',
    ogTitle: 'Авторизация | Most',
    description: 'Авторизация | Most',
    ogDescription: 'Авторизация | Most',
})
</script>
<style lang="scss" scoped>
.page {
    padding: 50px 20px 120px;
    background: url("@/assets/img/reg.png") no-repeat;
    height: 100vh;

    @media (max-width: 1600px) {
        height: auto;
    }

    .error {
        color: red;
        font-size: 14px;
        font-family: var(--int);
    }

    .form {
        display: flex;
        justify-content: center;
        margin-top: 35px;

        .form__body {
            background: #1E1E1E;
            box-shadow: 2px 2px 48px 10px rgba(0, 0, 0, 0.25) inset;
            padding: 44px 105px 30px;

            @media (max-width: 1024px) {
                padding: 10px 16px 15px;
                width: 100%;
            }

            .complete {
                button {
                    width: 100%;
                    padding: 10px 0;
                    border: 1px solid #f00;
                    background: transparent;
                    margin: 40px 0 20px;

                    font-size: 20px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: 130%;
                    letter-spacing: 0.2px;
                    text-transform: uppercase;
                    font-family: var(--int);
                    color: #fff;

                    @media (max-width: 1024px) {
                        font-size: 16px;
                        margin: 30px 0 20px;
                    }
                }

                span {
                    font-size: 16px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: normal;
                    font-family: var(--int);
                    color: #fff;

                    a {
                        color: #fff;
                        text-decoration: underline;
                    }
                }
            }

            .inputs {
                display: flex;
                flex-direction: column;
                gap: 30px;
                margin-top: 30px;

                @media (max-width: 1024px) {
                    gap: 15px;
                    margin-top: 20px;
                }

                div {
                    position: relative;

                    img {
                        position: absolute;
                        right: 5%;
                        top: 60%;
                        cursor: pointer;
                    }

                    input,
                    label {
                        display: block;
                    }

                    label {
                        font-size: 32px;
                        font-style: normal;
                        font-weight: 400;
                        line-height: normal;
                        text-transform: uppercase;
                        font-family: var(--tka);
                        color: #fff;
                        margin: 0 0 5px;

                        @media (max-width: 1024px) {
                            font-size: 20px;
                        }
                    }

                    input {
                        width: 100%;
                        border: 1px solid #fff;
                        background: transparent;
                        padding: 9px 10px;

                        font-size: 20px;
                        font-style: normal;
                        font-weight: 400;
                        line-height: 130%;
                        font-family: var(--int);
                        color: #fff;

                        @media (max-width: 1024px) {
                            font-size: 16px;
                        }
                    }
                }
            }

            .type {
                display: flex;
                gap: 20px;

                button {
                    flex: 1;
                    background: transparent;
                    border: 1px solid #fff;
                    padding: 13px 0;

                    font-size: 20px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: normal;
                    text-transform: uppercase;
                    font-family: var(--tka);
                    color: #fff;

                    @media (max-width: 1024px) {
                        font-size: 16px;
                    }
                }
            }

            h1 {
                font-size: 64px;
                font-style: normal;
                font-weight: 400;
                line-height: normal;
                text-transform: uppercase;
                font-family: var(--tka);
                color: #f00;
                text-align: center;

                @media (max-width: 1024px) {

                    font-size: 36px;
                }
            }
        }
    }
}
</style>