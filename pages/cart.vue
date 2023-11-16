<template>
    <div class="page">
        <prevPage></prevPage>
        <div class="empty" v-if="!test">
            <h1>Хэй, тут ничего. Оформим покупку?</h1>

            <div class="next">
                <NuxtLink to="/complete-order">
                    <img src="@/assets/img/nextbg.svg" class="bg" alt="">
                    В каталог
                    <img src="@/assets/img/next.svg" alt="">
                </NuxtLink>
            </div>
        </div>
        <div v-else>
            <div class="cart">
                <div class="cart__item">

                    <div class="img">
                        <img src="@/assets/img/cart.png" alt="">
                    </div>

                    <div class="item__info">
                        <div class="name">
                            <h2>Джинсы «Fases»</h2>
                            <span>34 555 ₸</span>
                            <small>S</small>
                        </div>

                        <div class="actions">
                            <p>S</p>
                            <div class="counter">
                                <small>-</small>
                                <span>1</span>
                                <small>+</small>
                            </div>

                            <img src="@/assets/img/trash.svg" alt="">
                        </div>
                    </div>
                </div>

                <div class="cart__item">

                    <div class="img">
                        <img src="@/assets/img/cart.png" alt="">
                    </div>

                    <div class="item__info">
                        <div class="name">
                            <h2>Кроссовки «Say Yes»</h2>
                            <span>34 555 ₸</span>
                            <small>S</small>
                        </div>

                        <div class="actions">
                            <p>S</p>
                            <div class="counter">
                                <small>-</small>
                                <span>1</span>
                                <small>+</small>
                            </div>

                            <img src="@/assets/img/trash.svg" alt="">
                        </div>
                    </div>
                </div>
                <div class="cart__item">

                    <div class="img">
                        <img src="@/assets/img/cart.png" alt="">
                    </div>

                    <div class="item__info">
                        <div class="name">
                            <h2>Топ «KRASIVO»</h2>
                            <span>34 555 ₸</span>
                            <small>S</small>
                        </div>

                        <div class="actions">
                            <p>S</p>
                            <div class="counter">
                                <small>-</small>
                                <span>1</span>
                                <small>+</small>
                            </div>

                            <img src="@/assets/img/trash.svg" alt="">
                        </div>
                    </div>
                </div>
            </div>

            <div class="total">
                <h2>Итого: 124 104 ₸ </h2>
            </div>


            <div class="next">
                <NuxtLink to="/complete-order">
                    <img src="@/assets/img/nextbg.svg" class="bg" alt="">
                    далее
                    <img src="@/assets/img/next.svg" alt="">
                </NuxtLink>
            </div>

        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            test: false,
        }
    }
}
</script>
<script setup>
useSeoMeta({
    title: 'Корзина | Most',
    ogTitle: 'Корзина | Most',
    description: 'Корзина | Most',
    ogDescription: 'Корзина | Most',
})
</script>
<style lang="scss" scoped>
.page {
    padding: 125px 100px 80px;

    @media (max-width: 1600px) {
        padding: 125px 50px 80px;
    }

    @media (max-width: 1024px) {
        padding: 125px 20px 50px;
    }

    .empty {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        gap: 50px;
        margin-top: 150px;
        text-align: center;

        h1 {
            font-size: 64px;
            font-style: normal;
            font-weight: 400;
            line-height: normal;
            font-family: var(--tka);
            color: #fff;
            margin: 0;

            @media (max-width: 1024px) {
                font-size: 22px;
            }
        }
    }

    .next {
        display: flex;
        justify-content: center;
        margin-top: 16px;

        @media (max-width: 1024px) {
            margin: 60px 0 40px;
        }

        a {
            font-size: 20px;
            font-style: normal;
            font-weight: 400;
            line-height: 130%;
            text-transform: uppercase;
            font-family: var(--int);
            color: #fff;
            text-decoration: none;
            position: relative;
            display: flex;
            align-items: center;
            gap: 5px;

            @media (max-width: 1024px) {
                font-size: 12px;
            }

            .bg {
                position: absolute;
                left: -40px;

                @media (max-width: 1024px) {
                    height: 78px;
                    width: 184px;
                    left: -50px;
                }
            }
        }
    }

    .total {
        margin-top: 40px;

        @media (max-width: 1024px) {
            margin-top: 30px;
        }

        h2 {
            font-size: 36px;
            font-style: normal;
            font-weight: 400;
            line-height: normal;
            font-family: var(--int);
            color: #fff;
            margin: 0;

            @media (max-width: 1024px) {
                font-size: 20px;
            }
        }
    }

    .cart {
        margin: 30px 0 0;
        display: flex;
        gap: 60px 110px;
        flex-wrap: wrap;

        @media (max-width: 1600px) {
            gap: 30px 60px;
        }

        @media (max-width: 1024px) {
            flex-direction: column;
            flex-wrap: nowrap;
            gap: 20px;
            margin: 20px 0 0;
        }

        .cart__item {
            display: flex;
            align-items: flex-start;
            gap: 40px;

            @media (max-width: 1600px) {
                gap: 25px;
            }

            @media (max-width: 1024px) {
                width: 100%;
                gap: 10px;
            }

            .item__info {
                height: 100%;
                display: flex;
                flex-direction: column;
                justify-content: space-between;
                align-items: flex-start;

                .actions {
                    display: flex;
                    align-items: center;
                    gap: 50px;

                    @media (max-width: 1600px) {
                        gap: 25px;
                        margin-top: 9px;
                    }

                    p {
                        padding: 10px 30px;
                        border: 1px solid #f00;

                        font-size: 16px;
                        font-style: normal;
                        font-weight: 400;
                        line-height: 130%;
                        font-family: var(--int);
                        color: #fff;
                        margin: 0;
                        display: none;

                        @media (max-width: 1024px) {
                            padding: 5px 10px;
                            display: block;
                        }
                    }

                    .counter {
                        display: flex;
                        gap: 30px;
                        align-items: center;

                        @media (max-width: 1024px) {
                            gap: 20px;
                        }

                        span {
                            font-size: 64px;
                            font-style: normal;
                            font-weight: 400;
                            line-height: normal;
                            font-family: var(--tka);
                            color: #fff;

                            @media (max-width: 1024px) {
                                font-size: 24px;
                            }
                        }

                        small {
                            font-size: 40px;
                            font-style: normal;
                            font-weight: 700;
                            line-height: normal;
                            font-family: var(--tka);
                            color: #fff;
                            cursor: pointer;

                            @media (max-width: 1024px) {
                                font-size: 24px;
                            }
                        }
                    }

                    img {
                        cursor: pointer;

                        @media (max-width: 1024px) {
                            width: 30px;
                            height: 30px;
                        }
                    }
                }

                .name {
                    display: flex;
                    gap: 20px;
                    flex-direction: column;
                    align-items: flex-start;

                    @media (max-width: 1024px) {
                        gap: 11px;
                    }

                    h2 {
                        font-size: 60px;
                        font-style: normal;
                        font-weight: 400;
                        line-height: normal;
                        font-family: var(--tka);
                        color: #fff;
                        margin: 0;
                        max-width: 400px;

                        @media (max-width: 1600px) {
                            font-size: 40px;
                        }

                        @media (max-width:1024px) {
                            font-size: 24px;
                            max-width: 100%;
                        }
                    }

                    span {
                        font-size: 40px;
                        font-style: normal;
                        font-weight: 400;
                        line-height: normal;
                        font-family: var(--int);
                        color: #fff;

                        @media (max-width: 1600px) {
                            font-size: 30px;
                        }

                        @media (max-width:1024px) {
                            font-size: 16px;
                        }
                    }

                    small {
                        padding: 10px 30px;
                        border: 1px solid #f00;

                        font-size: 16px;
                        font-style: normal;
                        font-weight: 400;
                        line-height: 130%;
                        font-family: var(--int);
                        color: #fff;

                        @media (max-width: 1024px) {
                            padding: 5px 10px;
                            display: none;
                        }
                    }
                }
            }

            .img {
                background: #000;
                border: 1px solid #f00;
                padding: 10px;

                img {
                    width: 300px;
                    height: 300px;
                    object-fit: cover;

                    @media (max-width: 1600px) {
                        width: 250px;
                        height: 250px;
                    }

                    @media (max-width: 1024px) {
                        width: 200px;
                        height: 200px;
                    }

                    @media (max-width: 500px) {
                        width: 80px;
                        height: 80px;
                    }
                }
            }
        }
    }
}
</style>