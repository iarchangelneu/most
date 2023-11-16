<template>
    <div class="page">
        <div class="username">
            <img src="@/assets/img/username.svg" alt="">
            <h1>рыскулова айжан</h1>
        </div>

        <div class="account">
            <div class="navigation">
                <span @click="selectedTab = 1" :class="{ activeSpan: selectedTab == 1 }">товары</span>
                <span @click="selectedTab = 2" :class="{ activeSpan: selectedTab == 2 }">продажи</span>
                <span @click="selectedTab = 3" :class="{ activeSpan: selectedTab == 3 }">баланс</span>
                <span @click="selectedTab = 4" :class="{ activeSpan: selectedTab == 4 }">настройки</span>
            </div>

            <div class="products" v-if="selectedTab == 1">
                <NuxtLink to="/create-product">добавить новый товар</NuxtLink>
                <div class="empty" v-if="!test"></div>

                <div class="products__body" v-else>
                    <div class="item">
                        <div class="img">
                            <img src="@/assets/img/product.png" alt="">
                        </div>

                        <div class="item__info">
                            <div>
                                <span class="d-block">джинсы клоунские 🤡</span>
                                <span class="d-block">19 070 ₸</span>
                            </div>

                            <div class="item__actions">
                                <img src="@/assets/img/pen.svg" alt="">
                                <img src="@/assets/img/bigeye.svg" alt="">
                            </div>
                        </div>
                    </div>
                    <div class="item">
                        <div class="img">
                            <img src="@/assets/img/product.png" alt="">
                        </div>

                        <div class="item__info">
                            <div>
                                <span class="d-block">джинсы клоунские 🤡</span>
                                <span class="d-block">19 070 ₸</span>
                            </div>

                            <div class="item__actions">
                                <img src="@/assets/img/pen.svg" alt="">
                                <img src="@/assets/img/bigeye.svg" alt="">
                            </div>
                        </div>
                    </div>
                    <div class="item">
                        <div class="img">
                            <img src="@/assets/img/product.png" alt="">
                        </div>

                        <div class="item__info">
                            <div>
                                <span class="d-block">джинсы клоунские 🤡</span>
                                <span class="d-block">19 070 ₸</span>
                            </div>

                            <div class="item__actions">
                                <img src="@/assets/img/pen.svg" alt="">
                                <img src="@/assets/img/bigeye.svg" alt="">
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="purchases" v-if="selectedTab == 2">
                <div class="empty" v-if="!test"></div>

                <div class="products__body" v-else>
                    <div class="why">
                        <div class="item">
                            <div class="img">
                                <img src="@/assets/img/product.png" alt="">
                            </div>

                            <div class="item__info">
                                <div>
                                    <span class="d-block">джинсы клоунские 🤡</span>
                                    <span class="d-block">19 070 ₸</span>
                                    <span class="d-block designmasterpc" style="text-transform: none;">Дата продажи:
                                        05.05.2023</span>
                                    <span class="d-block designmasterpc" style="text-transform: none;">e-mail покупателя:
                                        alexander.ivanov@gmail.com</span>
                                </div>

                                <div class="item__actions">
                                    <img src="@/assets/img/bigeye.svg" alt="">
                                </div>
                            </div>
                        </div>
                        <span class="d-block designmastermob" style="text-transform: none;">Дата продажи:
                            05.05.2023</span>
                        <span class="d-block designmastermob" style="text-transform: none;">e-mail покупателя:
                            alexander.ivanov@gmail.com</span>
                    </div>
                    <div class="why">
                        <div class="item">
                            <div class="img">
                                <img src="@/assets/img/product.png" alt="">
                            </div>

                            <div class="item__info">
                                <div>
                                    <span class="d-block">джинсы клоунские 🤡</span>
                                    <span class="d-block">19 070 ₸</span>
                                    <span class="d-block designmasterpc" style="text-transform: none;">Дата продажи:
                                        05.05.2023</span>
                                    <span class="d-block designmasterpc" style="text-transform: none;">e-mail покупателя:
                                        alexander.ivanov@gmail.com</span>
                                </div>

                                <div class="item__actions">
                                    <img src="@/assets/img/bigeye.svg" alt="">
                                </div>
                            </div>
                        </div>
                        <span class="d-block designmastermob" style="text-transform: none;">Дата продажи:
                            05.05.2023</span>
                        <span class="d-block designmastermob" style="text-transform: none;">e-mail покупателя:
                            alexander.ivanov@gmail.com</span>
                    </div>
                    <div class="why">
                        <div class="item">
                            <div class="img">
                                <img src="@/assets/img/product.png" alt="">
                            </div>

                            <div class="item__info">
                                <div>
                                    <span class="d-block">джинсы клоунские 🤡</span>
                                    <span class="d-block">19 070 ₸</span>
                                    <span class="d-block designmasterpc" style="text-transform: none;">Дата продажи:
                                        05.05.2023</span>
                                    <span class="d-block designmasterpc" style="text-transform: none;">e-mail покупателя:
                                        alexander.ivanov@gmail.com</span>
                                </div>

                                <div class="item__actions">
                                    <img src="@/assets/img/bigeye.svg" alt="">
                                </div>
                            </div>
                        </div>
                        <span class="d-block designmastermob" style="text-transform: none;">Дата продажи:
                            05.05.2023</span>
                        <span class="d-block designmastermob" style="text-transform: none;">e-mail покупателя:
                            alexander.ivanov@gmail.com</span>
                    </div>
                </div>
            </div>

            <TheTransactions v-if="selectedTab == 3"></TheTransactions>

            <div class="settings" v-if="selectedTab == 4">
                <div class="avatar">
                    <div class="img">
                        <div class="change__avatar">
                            <span>Изменить</span>
                        </div>
                        <img src="@/assets/img/ava.png" alt="">
                    </div>

                    <div class="buttons">
                        <button>сохранить</button>
                        <button>выход</button>
                    </div>
                </div>

                <div class="inputs">
                    <div>
                        <label for="name">Отображаемое имя</label>
                        <input type="text" id="name" name="name">
                    </div>
                    <div>
                        <label for="email">Эл. почта</label>
                        <input type="email" id="email" name="email">
                    </div>
                    <div>
                        <label for="password">Пароль</label>
                        <input type="password" id="password" name="password">
                    </div>
                </div>

                <div class="description">
                    <div>
                        <label for="tabs">Описание товара</label>
                        <ClientOnly>
                            <QuillEditor theme="bubble" toolbar="full" v-model:content="description" contentType="html" />
                        </ClientOnly>
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
            selectedTab: 4,
            test: true,
            description: '',
            remainingCharacters: 10,
        }
    },
    methods: {

    },
}
</script>
<script setup>
import { QuillEditor } from '@vueup/vue-quill';
import '@vueup/vue-quill/dist/vue-quill.snow.css';
import '@vueup/vue-quill/dist/vue-quill.bubble.css';

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
        margin: 40px 0 0;

        @media (max-width: 1024px) {
            flex-direction: column;
            justify-content: center;
            align-items: center;
            gap: 20px;
            margin: 30px 0 0;
        }

        .settings {
            display: flex;
            gap: 20px;
            flex-wrap: wrap;


            @media(max-width: 1024px) {
                flex-direction: column;
                width: 100%;
            }

            .description {
                width: 30.521vw;

                @media (max-width: 1400px) {
                    width: 100%;
                }


                label {
                    font-size: 20px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: 130%;
                    font-family: var(--int);
                    color: #fff;
                    margin: 0 0 10px;
                }
            }

            .inputs {
                margin: 0 0 0 30px;
                width: 21.615vw;
                display: flex;
                flex-direction: column;
                gap: 20px;

                @media (max-width: 1400px) {
                    width: 60.7%;
                }

                @media (max-width: 1024px) {
                    width: 100%;
                    margin: 0;
                }

                label,
                input {
                    display: block;
                }

                label {
                    font-size: 20px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: 130%;
                    font-family: var(--int);
                    color: #fff;
                    margin: 0 0 10px;
                }

                input {
                    background: transparent;
                    border: 1px solid #f00;
                    padding: 9px 10px;
                    width: 100%;

                    font-size: 20px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: 130%;
                    font-family: var(--int);
                    color: #fff;
                }
            }

            .avatar {
                display: flex;
                flex-direction: column;
                gap: 10px;

                .buttons {
                    display: flex;
                    flex-direction: column;
                    gap: 10px;

                    button {
                        background: transparent;
                        border: 1px solid #f00;
                        padding: 10px 0;

                        font-size: 16px;
                        font-style: normal;
                        font-weight: 400;
                        line-height: 130%;
                        /* 20.8px */
                        letter-spacing: 0.16px;
                        text-transform: uppercase;
                        font-family: var(--int);
                        color: #fff;

                        @media (max-width: 1024px) {
                            font-size: 12px;
                        }
                    }
                }

                .img {
                    background: #000;
                    border: 1px solid #f00;
                    padding: 10px;
                    position: relative;

                    &:hover .change__avatar {
                        opacity: 1;
                    }

                    .change__avatar {
                        position: absolute;
                        height: 100%;
                        width: 100%;
                        top: 0;
                        left: 0;

                        display: flex;
                        justify-content: center;
                        align-items: center;
                        flex-direction: column;
                        opacity: 0;
                        transition: all .3s ease;
                        background: rgba($color: #fff, $alpha: 0.2);

                        cursor: pointer;

                        span {
                            font-family: var(--int);
                            color: #fff;
                            font-size: 20px;
                            display: block;
                            text-decoration: underline;
                        }
                    }

                    img {
                        width: 240px;
                        height: 260px;
                        object-fit: cover;

                        @media (max-width: 1024px) {
                            width: 100%;
                        }
                    }
                }
            }
        }

        .purchases {
            width: 74%;

            @media (max-width: 1024px) {
                width: 100%;
                display: flex;
                justify-content: center;
                flex-direction: column;
                align-items: center;
            }

            button {
                margin: 0 0 30px;
                background: transparent;
                border: 1px solid #f00;
                padding: 10px 30px;

                font-size: 20px;
                font-style: normal;
                font-weight: 400;
                line-height: 130%;
                /* 26px */
                letter-spacing: 0.2px;
                text-transform: uppercase;
                font-family: var(--int);
                color: #fff;

                @media (max-width: 1024px) {
                    font-size: 12px;
                }
            }

            .products__body {
                display: grid;
                grid-template-columns: repeat(auto-fill, minmax(559px, 1fr));
                gap: 30px;
                grid-auto-flow: dense;

                @media (max-width: 1600px) {
                    grid-template-columns: repeat(auto-fill, minmax(480px, 1fr));
                }

                @media (max-width: 1024px) {
                    gap: 20px;
                    grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
                    width: 100%;
                }

                .why {
                    span {
                        font-size: 16px;
                        font-style: normal;
                        font-weight: 400;
                        line-height: normal;
                        text-transform: uppercase;
                        font-family: var(--int);
                        color: #fff;
                    }

                    .designmastermob {
                        display: none !important;

                        margin: 10px 0;

                        &:last-child {
                            margin: 0;
                        }

                        @media (max-width: 1024px) {
                            display: block !important;
                        }


                    }
                }

                .item {
                    display: flex;
                    align-items: flex-start;
                    gap: 20px;

                    @media (max-width: 1024px) {
                        gap: 15px;
                        width: 100%;
                    }

                    .item__info {
                        display: flex;
                        flex-direction: column;
                        height: 100%;

                        @media (max-width: 1024px) {
                            width: 100%;
                        }

                        .designmasterpc {
                            @media (max-width: 1024px) {
                                display: none !important;
                            }
                        }

                        .item__actions {
                            margin-top: auto;
                            display: flex;
                            justify-content: flex-start;
                            align-items: center;
                            gap: 20px;



                            img {
                                cursor: pointer;

                                @media (max-width: 1024px) {
                                    width: 30px;
                                    height: 30px;
                                }
                            }
                        }

                        span {
                            font-size: 16px;
                            font-style: normal;
                            font-weight: 400;
                            line-height: normal;
                            text-transform: uppercase;
                            font-family: var(--int);
                            color: #fff;
                            margin-bottom: 10px;

                            &:last-child {
                                margin: 0;
                            }
                        }
                    }

                    .img {
                        background: #000;
                        border: 1px solid #f00;
                        padding: 10px;

                        @media (max-width: 1024px) {
                            padding: 5px;
                        }

                        img {
                            width: 150px;
                            height: 150px;
                            object-fit: cover;

                            @media (max-width: 1024px) {
                                width: 80px;
                                height: 80px;
                            }
                        }
                    }
                }
            }
        }

        .products {
            width: 74%;

            @media (max-width: 1024px) {
                width: 100%;
                display: flex;
                justify-content: center;
                flex-direction: column;
                align-items: center;
            }

            a {
                margin: 0 0 30px;
                background: transparent;
                border: 1px solid #f00;
                padding: 10px 30px;
                text-decoration: none;
                display: inline-block;
                font-size: 20px;
                font-style: normal;
                font-weight: 400;
                line-height: 130%;
                /* 26px */
                letter-spacing: 0.2px;
                text-transform: uppercase;
                font-family: var(--int);
                color: #fff;

                @media (max-width: 1024px) {
                    font-size: 12px;
                }
            }

            .products__body {
                display: grid;
                grid-template-columns: repeat(auto-fill, minmax(391px, 1fr));
                gap: 30px;
                grid-auto-flow: dense;

                @media (max-width: 1024px) {
                    gap: 20px;
                    grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
                    width: 100%;
                }

                .item {
                    display: flex;
                    align-items: flex-start;
                    gap: 20px;

                    @media (max-width: 1024px) {
                        gap: 15px;
                        width: 100%;
                    }

                    .item__info {
                        display: flex;
                        flex-direction: column;
                        height: 100%;

                        @media (max-width: 1024px) {
                            width: 100%;
                        }

                        .item__actions {
                            margin-top: auto;
                            display: flex;
                            justify-content: flex-end;
                            align-items: center;
                            gap: 20px;



                            img {
                                cursor: pointer;

                                @media (max-width: 1024px) {
                                    width: 30px;
                                    height: 30px;
                                }
                            }
                        }

                        span {
                            font-size: 16px;
                            font-style: normal;
                            font-weight: 400;
                            line-height: normal;
                            text-transform: uppercase;
                            font-family: var(--int);
                            color: #fff;
                            margin-bottom: 10px;

                            &:last-child {
                                margin: 0;
                            }
                        }
                    }

                    .img {
                        background: #000;
                        border: 1px solid #f00;
                        padding: 10px;

                        @media (max-width: 1024px) {
                            padding: 5px;
                        }

                        img {
                            width: 150px;
                            height: 150px;
                            object-fit: cover;

                            @media (max-width: 1024px) {
                                width: 80px;
                                height: 80px;
                            }
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
                flex-wrap: wrap;
            }

            @media (max-width: 500px) {
                gap: 15px;
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