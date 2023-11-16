<template>
    <div class="page">
        <div class="text-center title">
            <prevPage class="back"></prevPage>
            <img src="@/assets/img/titlecover.png" class="cover" alt="">
            <h1>оформление заказа</h1>
            <div></div>
        </div>

        <div class="order__body">
            <div class="order__data">
                <div>
                    <label for="fio">ФИО</label>
                    <input type="text" id="fio" name="fio">
                </div>
                <div>
                    <label for="email">ЭЛЕКТРОННАЯ ПОЧТА</label>
                    <input type="email" id="email" name="email">
                </div>
                <div>
                    <label for="adress">аДРЕС ДОСТАВКИ</label>
                    <input type="text" id="adress" name="adress">
                </div>
                <div>
                    <label for="comment">кОММЕНТАРИЙ</label>
                    <textarea name="comment" id="comment" cols="30" rows="4"></textarea>
                </div>
            </div>

            <div class="order__items">
                <h2>СОСТАВ ЗАКАЗА</h2>
                <div class="order__items--body">
                    <div class="items">
                        <div class="item">
                            <img src="@/assets/img/fav1.png" alt="">
                        </div>
                        <div class="item">
                            <img src="@/assets/img/fav1.png" alt="">
                        </div>
                        <div class="item">
                            <img src="@/assets/img/fav1.png" alt="">
                        </div>
                        <div class="item">
                            <img src="@/assets/img/fav1.png" alt="">
                        </div>
                        <div class="item">
                            <img src="@/assets/img/fav1.png" alt="">
                        </div>
                        <div class="item">
                            <img src="@/assets/img/fav1.png" alt="">
                        </div>
                    </div>

                    <div class="total">
                        <span>6 ТОВАРОВ</span>
                        <span>154 896 ₸</span>
                    </div>
                </div>

                <div class="confirm">
                    <NuxtLink>
                        <img src="@/assets/img/defaultbg.svg" class="bg" alt="">
                        <span ref="complete">к оплате</span>
                        <img src="@/assets/img/next.svg">
                    </NuxtLink>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {

        }
    }
}
</script>
<script setup>
useSeoMeta({
    title: 'Оформление заказа | Most',
    ogTitle: 'Оформление заказа | Most',
    description: 'Оформление заказа | Most',
    ogDescription: 'Оформление заказа | Most',
})
</script>
<style lang="scss" scoped>
.page {
    padding: 125px 0 100px;

    @media (max-width: 1024px) {
        padding: 125px 0 50px;
    }

    .order__body {
        margin-top: 20px;
        display: flex;
        gap: 150px;
        align-items: flex-start;
        padding: 0 100px;


        @media (max-width: 1600px) {
            padding: 0 50px;
            gap: 70px;
        }

        @media (max-width: 1024px) {
            padding: 0 20px;
            gap: 40px;
            flex-direction: column;
        }

        .order__items {
            width: 100%;

            .confirm {
                margin-top: 70px;

                @media (max-width: 1024px) {
                    display: flex;
                    justify-content: center;
                    margin: 100px 0 40px;
                }

                a {
                    font-size: 20px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: 130%;
                    cursor: pointer;
                    text-transform: uppercase;
                    font-family: var(--int);
                    color: #fff;
                    text-decoration: none;

                    display: flex;
                    gap: 5px;
                    align-items: center;

                    position: relative;

                    @media (max-width: 1024px) {
                        font-size: 12px;
                    }

                    .bg {
                        position: absolute;
                        left: -20px;

                        @Media (max-width: 1024px) {
                            left: -40px;
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

            .order__items--body {
                border: 1px solid #f00;
                padding: 20px 20px 54px;


                @media(max-width: 1024px) {
                    padding: 15px 15px 12px;
                }

                .total {
                    display: flex;
                    flex-direction: column;
                    gap: 20px;
                    margin-top: 30px;

                    @media (max-width: 1024px) {
                        gap: 10px;
                        margin-top: 15px;
                    }

                    span {
                        font-size: 20px;
                        font-style: normal;
                        font-weight: 400;
                        line-height: normal;
                        font-family: var(--int);
                        color: #fff;

                        @media (max-width: 1024px) {
                            font-size: 16px;
                        }
                    }
                }

                .items {
                    display: grid;
                    grid-template-columns: repeat(auto-fill, minmax(169px, 1fr));
                    gap: 20px;
                    grid-auto-flow: dense;

                    @media (max-width: 1024px) {
                        grid-template-columns: repeat(auto-fill, minmax(99px, 1fr));
                        gap: 10px;
                    }

                    .item {
                        padding: 10px;
                        background: #000;
                        border: 1px solid #f00;

                        img {
                            width: 100%;
                            height: 150px;
                            object-fit: cover;

                            @media (max-width: 1024px) {
                                height: 80px;
                            }
                        }
                    }
                }
            }

            h2 {
                font-size: 48px;
                font-style: normal;
                font-weight: 400;
                line-height: normal;
                font-family: var(--tka);
                color: #fff;
                margin: 0 0 10px;

                @media (max-width: 1024px) {
                    font-size: 32px;
                }
            }
        }

        .order__data {
            width: 100%;
            max-width: 600px;
            display: flex;
            flex-direction: column;
            gap: 30px;

            @media (max-width: 1600px) {
                max-width: 450px;
            }

            @media (max-width: 1024px) {
                max-width: 100%;
                gap: 20px;
            }

            input,
            label {
                display: block;
            }

            input,
            textarea {
                width: 100%;
                background: #480000;
                border: 1px solid #f00;
                padding: 10px 15px;

                font-size: 20px;
                font-style: normal;
                font-weight: 400;
                line-height: normal;
                font-family: var(--int);
                color: #fff;

                @media (max-width: 1024px) {
                    font-size: 16px;
                    padding: 10px;
                }
            }

            label {
                font-size: 48px;
                font-style: normal;
                font-weight: 400;
                line-height: normal;
                font-family: var(--tka);
                color: #fff;
                margin: 0 0 10px;

                @media (max-width: 1024px) {
                    font-size: 32px;
                }
            }
        }
    }

    .title {
        position: relative;
        display: flex;
        justify-content: space-between;
        align-items: center;

        .cover {
            position: absolute;
            bottom: -25px;
            left: 0;
            z-index: 1;

            @media (max-width: 1024px) {
                display: none;
            }
        }

        .back {
            margin-left: 100px;
            z-index: 2;

            @media (max-width: 1600px) {
                margin-left: 50px;
            }

            @media (max-width: 1024px) {
                margin-left: 20px;
            }
        }

        h1 {
            position: relative;
            font-size: 64px;
            font-style: normal;
            font-weight: 400;
            line-height: normal;
            text-transform: uppercase;
            font-family: var(--tka);
            color: #fff;
            margin: 0;
            z-index: 3;

            margin-left: -100px;

            @media (max-width: 1024px) {
                font-size: 36px;
                display: none;
            }
        }
    }
}
</style>