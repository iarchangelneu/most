<template>
    <div class="page">
        <div class="form">
            <div class="links" v-if="accountType == 'buyer'">
                <NuxtLink to="/withdrawal">
                    вывод
                </NuxtLink>
                <NuxtLink to="/refill">
                    пополнение
                </NuxtLink>
            </div>

            <div class="form__body">
                <h1>Порядок действий для пополнения баланса</h1>

                <p>1. Подтвердите Ваше согласие с правилами системы</p>

                <label class="custom-checkbox">
                    <input type="checkbox">
                    <p class="checkbox-text m-0">Я согласен с <NuxtLink to="/terms">пользовательским соглашением</NuxtLink>
                        и
                        <NuxtLink to="/polytics">политикой конфиденциальности</NuxtLink>
                    </p>
                </label>

                <p>2. Введите сумму, на которую вы хотите пополнить личный счёт, и нажмите на кнопку «Пополнить». Вы будете
                    переадресованы на сайт платёжной системы, где сможете завершить платёж.</p>

                <div class="complete">
                    <input type="number" v-model="cost">
                    <button ref="inBtn" @click="inMoney">пополнить</button>
                </div>

                <div class="selects">
                    <button @click="cost = 100" :style="{ 'border': cost == 100 ? '1px solid #f00' : '1px solid #fff' }">100
                        ₸</button>
                    <button @click="cost = 1000"
                        :style="{ 'border': cost == 1000 ? '1px solid #f00' : '1px solid #fff' }">1000 ₸</button>
                    <button @click="cost = 2000"
                        :style="{ 'border': cost == 2000 ? '1px solid #f00' : '1px solid #fff' }">2000 ₸</button>
                    <button @click="cost = 5000"
                        :style="{ 'border': cost == 5000 ? '1px solid #f00' : '1px solid #fff' }">5000 ₸</button>
                    <button @click="cost = 10000"
                        :style="{ 'border': cost == 10000 ? '1px solid #f00' : '1px solid #fff' }">10000 ₸</button>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import global from '~/mixins/global';
import axios from 'axios'
export default {
    mixins: [global],
    data() {
        return {
            cost: null,
            pathUrl: 'https://mostshop.kz',
            accountType: '',
        }
    },
    methods: {
        inMoney() {
            const token = this.getAuthorizationCookie()
            const csrf = this.getCSRFToken()
            const path = `${this.pathUrl}/api/money/new-pay`
            axios.defaults.headers.common['Authorization'] = `Token ${token}`;
            axios.defaults.headers.common['X-CSRFToken'] = csrf;
            this.$refs.inBtn.innerHTML = 'ОЖИДАЙТЕ'

            axios
                .post(path, {
                    amount: this.cost
                })
                .then(response => {
                    console.log(response)
                    window.location.href = response.data.url
                    if (response.status = 201) {
                        this.$refs.inBtn.innerHTML = 'ПОПОЛНИТЬ'
                    }
                    if (response.status == 228) {
                        this.$refs.outBtn.innerHTML = response.data.error_msg
                    }
                })
                .catch(error => {
                    console.error(error)
                    this.$refs.inBtn.innerHTML = 'ПОПОЛНИТЬ'
                })
        },
    },
    mounted() {
        const accType = localStorage.getItem('accountType')
        if (accType !== 'buyer-account' && accType !== 'seller-account') {
            window.location.href = '/login'
        }
        if (accType == 'buyer-account') {
            this.accountType = 'buyer'

        }
        else if (accType == 'seller-account') {
            this.accountType = 'seller'
        }
        else {
            return
        }

    }
}
</script>
<script setup>
useSeoMeta({
    title: 'Пополнение счета | Most',
    ogTitle: 'Пополнение счета | Most',
    description: 'Пополнение счета | Most',
    ogDescription: 'Пополнение счета | Most',
})
</script>
<style lang="scss" scoped>
.page {
    display: flex;
    padding: 125px 0 50px;
    justify-content: center;
    align-items: center;
    flex-direction: column;

    @media (max-width: 1024px) {
        padding: 125px 20px 50px;
    }

    .form {
        background: #480000;
        border: 1px solid #f00;
        padding: 30px;

        @media (max-width: 1024px) {
            padding: 20px 15px;
        }

        .form__body {
            display: flex;
            flex-direction: column;
            gap: 20px;
            margin-top: 20px;

            @media (max-width: 1024px) {
                gap: 13px;
            }

            .selects {
                display: flex;
                flex-wrap: wrap;
                justify-content: center;
                gap: 10px;

                @media (max-width: 1024px) {
                    gap: 16px;
                }

                button {
                    background: transparent;
                    border: 1px solid #fff;
                    padding: 13px;

                    font-size: 20px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: normal;
                    font-family: var(--int);
                    color: #fff;
                }
            }

            .complete {
                display: flex;
                gap: 20px;

                input {
                    flex: 1;
                    max-width: 227px;

                    padding: 12px;
                    text-align: right;

                    border: 1px solid #fff;
                    background: transparent;

                    font-size: 20px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: 130%;
                    font-family: var(--int);
                    color: #fff;

                    @media (max-width: 1024px) {
                        max-width: 150px;
                    }
                }

                button {
                    flex: 1;
                    background: transparent;
                    border: 1px solid #f00;
                    text-align: center;
                    padding: 10px 0;

                    font-size: 24px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: 130%;
                    font-family: var(--tka);
                    color: #fff;
                }
            }

            input {
                border: 1px solid #fff;
                padding: 12px 10px;
                background: transparent;

                font-size: 20px;
                font-style: normal;
                font-weight: 400;
                line-height: 130%;
                font-family: var(--int);
                color: #fff;

                @media (max-width: 1024px) {
                    font-size: 16px;
                }

                &::placeholder {
                    color: #935757;
                }
            }

            h1 {
                text-align: center;
                font-size: 20px;
                font-style: normal;
                font-weight: 400;
                line-height: 130%;
                font-family: var(--int);
                color: #fff;
                margin: 0;

                @media(max-width: 1024px) {
                    font-size: 16px;
                }
            }

            p,
            a {
                font-size: 16px;
                font-style: normal;
                font-weight: 400;
                line-height: 130%;
                font-family: var(--int);
                color: #fff;
                margin: 0;
                max-width: 512px;

            }

            a {
                text-decoration: underline;
            }
        }

        .links {
            display: flex;
            justify-content: center;
            gap: 30px;

            a {
                font-size: 24px;
                font-style: normal;
                font-weight: 400;
                line-height: normal;
                font-family: var(--tka);
                color: #fff;
                text-decoration: none;

                padding: 10px 30px;
                border: 1px solid #fff;

                &:last-child {
                    border: 1px solid #f00;
                }
            }
        }
    }
}

.custom-checkbox p,
.custom-checkbox a {
    @media (max-width: 1024px) {
        font-size: 12px !important;
    }
}

.custom-checkbox input[type="checkbox"] {
    opacity: 0;
    position: absolute;
    border-radius: 3px;
}

.custom-checkbox .checkbox-text:before {
    content: '';
    display: inline-block;
    vertical-align: middle;
    width: 30px;
    height: 30px;
    margin-right: 10px;
    border: 1px solid #fff;
    border-radius: 0;
    margin-bottom: 3px;
}

.custom-checkbox input[type="checkbox"]:checked+.checkbox-text:before {
    content: url('@/assets/img/check.svg');
    font-size: 30px;
    color: black;
    text-align: center;
    line-height: 20px;
    background: transparent;
}

.custom-checkbox:last-child {
    margin-bottom: 0 !important;

    @media (max-width: 1024px) {
        margin-bottom: 22px !important;
    }
}
</style>