<template>
    <div class="page">
        <div class="username">
            <img src="@/assets/img/username.svg" alt="">
            <h1>USERNAME2020@GMAIL.COM</h1>
        </div>

        <div class="account">
            <div class="navigation">
                <span @click="selectedTab = 1" :class="{ activeSpan: selectedTab == 1 }">Заказы</span>
                <span @click="selectedTab = 2" :class="{ activeSpan: selectedTab == 2 }">баланс</span>
                <span @click="selectedTab = 3" :class="{ activeSpan: selectedTab == 3 }">настройки</span>
            </div>
            <div v-if="selectedTab == 1 && !test" class="text-center w-100 empty">
                <h1>У ВАС ПОКА НЕТ ЗАКАЗОВ</h1>

                <NuxtLink to="/catalog">
                    <img src="@/assets/img/defaultbg.svg" class="bg" alt="">
                    <span>В каталог</span>
                    <img src="@/assets/img/next.svg" alt="">
                </NuxtLink>
            </div>
            <div class="orders" v-if="selectedTab == 1 && test">
                <div class="order">
                    <div class="order__items">
                        <div class="item">
                            <img src="@/assets/img/order.png" alt="">
                        </div>
                        <div class="item">
                            <img src="@/assets/img/order.png" alt="">
                        </div>

                        <div class="item">
                            <img src="@/assets/img/order.png" alt="">
                        </div>
                        <div class="item">
                            <img src="@/assets/img/order.png" alt="">
                        </div>
                        <div class="item">
                            <img src="@/assets/img/order.png" alt="">
                        </div>

                    </div>

                    <div class="order__details">
                        <span>10 ТОВАРОВ</span>
                        <span>154 896 ₸</span>
                        <span>23.08.2023</span>
                    </div>
                </div>
                <div class="order">
                    <div class="order__items">
                        <div class="item">
                            <img src="@/assets/img/order.png" alt="">
                        </div>
                        <div class="item">
                            <img src="@/assets/img/order.png" alt="">
                        </div>
                        <div class="item">
                            <img src="@/assets/img/order.png" alt="">
                        </div>
                        <div class="item">
                            <img src="@/assets/img/order.png" alt="">
                        </div>
                        <div class="item">
                            <img src="@/assets/img/order.png" alt="">
                        </div>


                    </div>

                    <div class="order__details">
                        <span>10 ТОВАРОВ</span>
                        <span>154 896 ₸</span>
                        <span>23.08.2023</span>
                    </div>
                </div>
                <div class="order">
                    <div class="order__items">
                        <div class="item">
                            <img src="@/assets/img/order.png" alt="">
                        </div>
                        <div class="item">
                            <img src="@/assets/img/order.png" alt="">
                        </div>
                        <div class="item">
                            <img src="@/assets/img/order.png" alt="">
                        </div>

                    </div>

                    <div class="order__details">
                        <span>10 ТОВАРОВ</span>
                        <span>154 896 ₸</span>
                        <span>23.08.2023</span>
                    </div>
                </div>
                <div class="order">
                    <div class="order__items">
                        <div class="item">
                            <img src="@/assets/img/order.png" alt="">
                        </div>


                    </div>

                    <div class="order__details">
                        <span>10 ТОВАРОВ</span>
                        <span>154 896 ₸</span>
                        <span>23.08.2023</span>
                    </div>
                </div>
                <div class="order">
                    <div class="order__items">
                        <div class="item">
                            <img src="@/assets/img/order.png" alt="">
                        </div>
                        <div class="item">
                            <img src="@/assets/img/order.png" alt="">
                        </div>
                        <div class="item">
                            <img src="@/assets/img/order.png" alt="">
                        </div>


                    </div>

                    <div class="order__details">
                        <span>10 ТОВАРОВ</span>
                        <span>154 896 ₸</span>
                        <span>23.08.2023</span>
                    </div>
                </div>
                <div class="order">
                    <div class="order__items">
                        <div class="item">
                            <img src="@/assets/img/order.png" alt="">
                        </div>

                    </div>

                    <div class="order__details">
                        <span>10 ТОВАРОВ</span>
                        <span>154 896 ₸</span>
                        <span>23.08.2023</span>
                    </div>
                </div>
            </div>

            <TheTransactions v-if="selectedTab == 2"></TheTransactions>


            <div class="settings" v-if="selectedTab == 3">
                <h2>Сменить пароль</h2>

                <div class="inputs">
                    <div>
                        <label for="current-password">Текущий пароль</label>
                        <input type="password" name="current-password" id="current-password">
                    </div>
                    <div>
                        <label for="new-password">Новый пароль</label>
                        <input type="password" name="new-password" id="new-password">
                    </div>
                    <div class="change">
                        <div>
                            <label for="repeat-password">Повторите пароль</label>
                            <input type="password" name="repeat-password" id="repeat-password">
                        </div>

                        <div class="buttons">
                            <button>сохранить</button>
                            <button>Выйти</button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            selectedTab: 1,
            test: true,
        }
    }
}
</script>
<script setup>
useSeoMeta({
    title: 'Личный кабинет | Most',
    ogTitle: 'Личный кабинет | Most',
    description: 'Личный кабинет | Most',
    ogDescription: 'Личный кабинет | Most',
})
</script>
<style lang="scss" scoped>
.page {
    padding: 125px 100px 100px;

    @media (max-width: 1600px) {
        padding: 125px 50px 100px;
    }

    @media (max-width: 1024px) {
        padding: 125px 20px 50px;
    }

    .account {
        display: flex;
        justify-content: space-between;
        align-items: flex-start;
        gap: 20px;
        margin: 40px 0 0;

        @media (max-width: 1024px) {
            flex-direction: column;
            justify-content: center;
            align-items: center;
            gap: 20px;
            margin: 30px 0 0;
        }

        .settings {
            @media (max-width: 1024px) {
                width: 100%;
            }

            h2 {
                font-size: 40px;
                font-style: normal;
                font-weight: 400;
                line-height: normal;
                font-family: var(--tka);
                color: #fff;
                margin: 0 0 20px;

                @media (max-width: 1024px) {
                    font-size: 24px;
                }
            }

            div {
                @media (max-width: 1024px) {
                    width: 100%;
                }
            }

            .inputs {
                display: flex;
                gap: 30px;
                align-items: flex-start;

                @media (max-width: 1300px) {
                    flex-direction: column;
                    gap: 20px;
                }

                .change {
                    display: flex;
                    flex-direction: column;
                    align-items: flex-end;
                    gap: 30px;

                    .buttons {
                        display: flex;
                        flex-direction: column;
                        gap: 30px;

                        @media (max-width: 1024px) {
                            width: auto;
                        }

                        button {
                            border: 1px solid #f00;
                            background: transparent;
                            padding: 10px 30px;

                            font-style: normal;
                            font-weight: 400;
                            line-height: 130%;
                            /* 26px */
                            letter-spacing: 0.2px;
                            text-transform: uppercase;
                            font-family: var(--int);
                            color: #fff;
                            font-size: 20px;

                            @media (max-width: 1024px) {
                                font-size: 12px;
                            }
                        }
                    }
                }

                input,
                label {
                    display: block;
                }

                label {
                    font-size: 20px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: normal;
                    font-family: var(--int);
                    color: #fff;
                    margin: 0 0 10px;

                    @media (max-width: 1024px) {
                        font-size: 16px;
                    }
                }

                input {
                    border: 1px solid #f00;
                    background: transparent;
                    padding: 9px 10px;

                    font-size: 20px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: normal;
                    font-family: var(--int);
                    color: #fff;

                    @media (max-width: 1024px) {
                        width: 100%;
                    }
                }
            }
        }

        .empty {
            display: flex;
            justify-content: center;
            flex-direction: column;
            align-items: center;
            gap: 60px;
            margin-top: 100px;

            @media (max-width: 1024px) {
                margin-top: 20px;
                gap: 50px;
            }

            h1 {
                font-size: 40px;
                font-style: normal;
                font-weight: 400;
                line-height: normal;
                font-family: var(--tka);
                color: #fff;
                margin: 0;

                @media (max-width: 1024px) {
                    font-size: 20px;
                }
            }

            a {
                font-size: 20px;
                font-style: normal;
                font-weight: 400;
                line-height: 130%;
                /* 26px */
                text-transform: uppercase;
                font-family: var(--int);
                color: #fff;
                text-decoration: none;

                display: flex;
                gap: 5px;
                align-items: center;

                position: relative;

                @media (max-width:1024px) {
                    font-size: 12px;
                }

                .bg {
                    position: absolute;
                    right: 0;

                    @media (max-width: 1024px) {
                        width: 100%;
                        left: -20px;
                    }
                }

                &:hover img {
                    opacity: 1;
                }

                img {
                    transition: all .3s ease;
                    opacity: 0;
                }
            }
        }

        .orders {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 20px;
            grid-auto-flow: dense;
            width: 80%;

            @media (max-width: 1024px) {
                width: 100%;
                grid-template-columns: repeat(auto-fill, minmax(165px, 1fr));
            }

            .order {
                border: 1px solid #f00;
                padding: 20px;
                display: flex;
                flex-direction: column;

                @media (max-width: 1024px) {
                    padding: 10px;
                }

                .order__items {
                    display: grid;
                    grid-template-columns: repeat(auto-fill, minmax(99px, 1fr));
                    gap: 10px;
                    grid-auto-flow: dense;
                    margin: 0 0 20px;

                    @media (max-width:1024px) {
                        grid-template-columns: repeat(auto-fill, minmax(69px, 1fr));
                        gap: 5px;
                        margin: 0 0 10px;
                    }

                    .item {
                        background: #000;
                        padding: 10px;
                        border: 1px solid #f00;

                        @media (max-width: 1024px) {
                            padding: 5px;
                        }

                        img {
                            width: 100%;
                            height: 80px;
                            object-fit: cover;

                            @media (max-width: 1024px) {
                                height: 60px;
                            }
                        }
                    }
                }

                .order__details {
                    display: flex;
                    flex-direction: column;
                    gap: 10px;
                    margin-top: auto;

                    span {
                        font-size: 16px;
                        font-style: normal;
                        font-weight: 400;
                        line-height: normal;
                        font-family: var(--int);
                        color: #fff;

                        @media (max-width: 1024px) {
                            font-size: 12px;
                        }
                    }
                }
            }
        }

        .navigation {
            display: flex;
            flex-direction: column;
            gap: 30px;

            @media (max-width: 1024px) {
                flex-direction: row;
                gap: 35px;
                justify-content: center;
            }

            .activeSpan {
                color: #f00;
            }

            span {
                font-size: 48px;
                font-style: normal;
                font-weight: 400;
                line-height: normal;
                font-family: var(--tka);
                color: #fff;
                cursor: pointer;

                @media (max-width: 1024px) {
                    font-size: 20px;
                }
            }
        }
    }

    .username {
        display: flex;
        gap: 20px;
        align-items: center;

        img {
            transition: all .3s ease;
            animation: rotateAnimation 2s linear infinite alternate;
        }

        @keyframes rotateAnimation {
            0% {
                transform: rotate3d(1, 1, 1, 0deg);
            }

            100% {
                transform: rotate3d(1, 1, 1, 35deg);
            }
        }

        h1 {
            font-size: 48px;
            font-style: normal;
            font-weight: 400;
            line-height: normal;
            font-family: var(--tka);
            color: #fff;
            margin: 0;

            @media (max-width: 1024px) {
                font-size: 20px;

            }
        }
    }
}
</style>