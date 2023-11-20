<template>
    <div class="page">
        <prevPage></prevPage>
        <div class="empty" v-if="cart.length <= 0">
            <h1>Хэй, тут ничего. Оформим покупку?</h1>

            <div class="next">
                <NuxtLink to="/catalog">
                    <img src="@/assets/img/nextbg.svg" class="bg" alt="">
                    В каталог
                    <img src="@/assets/img/next.svg" alt="">
                </NuxtLink>
            </div>
        </div>
        <div v-else>
            <div class="cart">
                <div class="cart__item" v-for="item in cart" :key="item.id">

                    <div class="img">
                        <img src="@/assets/img/cart.png" alt="">
                    </div>

                    <div class="item__info">
                        <div class="name">
                            <h2>Джинсы «Fases»</h2>
                            <span>{{ (item.products.price * item.amount).toLocaleString() }} ₸</span>
                            <small>{{ item.size }}</small>
                        </div>

                        <div class="actions">
                            <p>{{ item.size }}</p>
                            <div class="counter">
                                <small @click="decreaseAmount(item.id)">-</small>
                                <span>{{ item.amount }}</span>
                                <small @click="increaseAmount(item.id)">+</small>
                            </div>

                            <img src="@/assets/img/trash.svg" @click="deleteFromCart(item.id)" alt="">
                        </div>
                    </div>
                </div>

            </div>

            <div class="total">
                <h2>Итого: {{ formatPrice(calculateTotal()) }} ₸ </h2>
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
import global from '~/mixins/global';
import axios from 'axios'
export default {
    mixins: [global],
    data() {
        return {
            test: false,
            cart: [],
            pathUrl: 'https://mostshop.kz',
        }
    },
    methods: {
        decreaseAmount(itemId) {
            const item = this.cart.find(item => item.id === itemId);
            if (item && item.amount > 0) {
                item.amount--;

                // Используем Vue.nextTick() для обновления данных после изменения
                this.$nextTick(() => {
                    if (item.amount <= 0) {
                        this.deleteFromCart(itemId);
                    }
                });
            }
        },
        increaseAmount(itemId) {
            const item = this.cart.find(item => item.id === itemId);
            if (item) {
                item.amount++;
            }
        },
        calculateTotal() {
            let total = 0;

            this.cart.forEach(item => {
                const { price, discount } = item.products;
                const discountedPrice = price * (1 - discount / 100);
                total += discountedPrice * item.amount;
            });

            return total;
        },
        formatPrice(price) {
            return Math.floor(price).toLocaleString();
        },
        deleteFromCart(id) {
            const token = this.getAuthorizationCookie()
            const csrf = this.getCSRFToken()
            const path = `${this.pathUrl}/api/buyer/delete-product-basket/${id}`
            axios.defaults.headers.common['Authorization'] = `Token ${token}`;
            axios.defaults.headers.common['X-CSRFToken'] = csrf;
            axios
                .put(path)
                .then(response => {
                    console.log(response)
                    this.getCart()
                })
                .catch(error => {
                    console.error(error)
                })
        },
        getCart() {
            const token = this.getAuthorizationCookie()
            const path = `${this.pathUrl}/api/buyer/all-product-basket`;
            axios.defaults.headers.common['Authorization'] = `Token ${token}`;

            axios
                .get(path)
                .then(response => {
                    this.cart = response.data
                })
                .catch(error => {
                    console.error(error)
                })
        },
    },
    mounted() {
        this.getCart()
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