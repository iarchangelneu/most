<template>
    <div class="page">
        <prevPage></prevPage>

        <div class="author">
            <div class="avatar">
                <img src="@/assets/img/bigava.png" alt="">
            </div>

            <div class="description">
                <h1>
                    рыскулова айжан
                    <img src="@/assets/img/flower.svg" alt="">
                </h1>

                <h2>Обо мне:</h2>
                <div class="desc" v-html="description"></div>
            </div>
        </div>


        <div class="author__products">
            <h1>товары продавца:</h1>

            <div class="catalog">
                <NuxtLink :to="'/product/' + 1" class="catalog__item">
                    <div class="img">
                        <div class="item__adv">
                            <div class="buttons">
                                <img src="@/assets/img/addcart.svg" alt="">
                                <img src="@/assets/img/addfav.svg" alt="">
                            </div>
                        </div>
                        <img src="@/assets/img/pop1.png" alt="">
                    </div>
                    <p>Джинсы «Fases»</p>

                    <div class="text-right">
                        <span> 34 555 ₸</span>
                    </div>
                </NuxtLink>
                <NuxtLink :to="'/product/' + 1" class="catalog__item">
                    <div class="img">
                        <div class="item__adv">
                            <div class="buttons">
                                <img src="@/assets/img/addcart.svg" alt="">
                                <img src="@/assets/img/addfav.svg" alt="">
                            </div>
                        </div>
                        <img src="@/assets/img/pop2.png" alt="">
                    </div>

                    <p>Кроссовки «Say Yes»</p>

                    <div class="text-right">
                        <span> 57 999 ₸</span>
                    </div>
                </NuxtLink>
                <NuxtLink :to="'/product/' + 1" class="catalog__item">
                    <div class="img">
                        <div class="item__adv">
                            <div class="buttons">
                                <img src="@/assets/img/addcart.svg" alt="">
                                <img src="@/assets/img/addfav.svg" alt="">
                            </div>
                        </div>
                        <img src="@/assets/img/pop3.png" alt="">
                    </div>

                    <p>Куртка «JO»</p>

                    <div class="text-right">
                        <span> 122 940 ₸</span>
                    </div>
                </NuxtLink>
                <NuxtLink :to="'/product/' + 1" class="catalog__item">
                    <div class="img">
                        <div class="item__adv">
                            <div class="buttons">
                                <img src="@/assets/img/addcart.svg" alt="">
                                <img src="@/assets/img/addfav.svg" alt="">
                            </div>
                        </div>
                        <img src="@/assets/img/pop4.png" alt="">
                    </div>

                    <p>Топ «KRASIVO»</p>

                    <div class="text-right">
                        <span> 31 550 ₸</span>
                    </div>
                </NuxtLink>
                <NuxtLink :to="'/product/' + 1" class="catalog__item">
                    <div class="img">
                        <div class="item__adv">
                            <div class="buttons">
                                <img src="@/assets/img/addcart.svg" alt="">
                                <img src="@/assets/img/addfav.svg" alt="">
                            </div>
                        </div>
                        <img src="@/assets/img/pop5.png" alt="">
                    </div>

                    <p>Рубашка «Art»</p>

                    <div class="text-right">
                        <span> 18 370 ₸</span>
                    </div>
                </NuxtLink>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            description: 'Привет, меня зовут Айжан Рыскулова, и я — творческий дух, воплощающий свой стиль через одежду. Моя миссия — помочь вам выразить индивидуальность через моду, и создать уникальные образы, которые отражают ваш характер и внутренний мир. <br> <br> Мои творения — это искусство, выраженное через текстиль. Каждая деталь, каждая ткань и каждый шов тщательно продуманы, чтобы придать вам уверенность и комфорт. Я работаю с разнообразными материалами, цветами и фактурами, чтобы создать уникальные наряды, которые подчёркивают ваш стиль. <br> <br> Будь то повседневная одежда, наряд для особого случая или что‑то между ними, я готова воплотить ваши мечты в реальность. Моя цель — сделать вашу одежду неотъемлемой частью вашей личности. <br><br> Покупая мои изделия, вы получаете не просто одежду, а часть меня и моего вдохновения. Всех обнимаю!'
        }
    }
}
</script>
<script setup>
useSeoMeta({
    title: 'Страница автора | Most',
    ogTitle: 'Страница автора | Most',
    description: 'Страница автора | Most',
    ogDescription: 'Страница автора | Most',
})
</script>
<style lang="scss" scoped>
.page {
    padding: 125px 150px 100px 100px;

    @media (max-width: 1600px) {
        padding: 125px 50px 100px;
    }

    @media (max-width: 1024px) {
        padding: 125px 20px 50px;
    }

    .author__products {
        margin-top: 50px;

        @media (max-width: 1024px) {
            margin-top: 30px;
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
                font-size: 32px;
            }
        }

        .catalog {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(310px, 1fr));
            gap: 30px;
            grid-auto-flow: dense;
            margin: 30px 0 0;

            @media (max-width: 1024px) {
                gap: 20px;
                grid-template-columns: repeat(auto-fill, minmax(165px, 1fr));
                margin: 20px 0 0;
            }

            .catalog__item {
                background: #000;
                padding: 10px;
                text-decoration: none;
                position: relative;

                .img {
                    position: relative;
                }

                .img:hover .item__adv {
                    opacity: 1;
                }

                .item__adv {
                    height: 100%;
                    width: 100%;
                    position: absolute;
                    opacity: 0;
                    left: 0;
                    top: 0;
                    transition: all .3s ease;

                    background: #00000073;
                    display: flex;
                    justify-content: center;
                    flex-direction: column;
                    align-items: center;

                    .buttons {
                        display: flex;
                        gap: 60px;

                        @media (max-width:1024px) {
                            gap: 20px;
                        }

                        img {
                            width: 60px;
                            height: 50px;
                        }
                    }
                }

                p,
                span {
                    font-size: 20px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: normal;
                    font-family: var(--int);
                    color: #fff;

                    @media (max-width: 1024px) {
                        font-size: 12px;
                    }
                }

                p {
                    margin: 10px 0;
                }

                img {
                    width: 100%;
                    height: 400px;
                    object-fit: cover;
                    pointer-events: none;

                    @media (max-width: 1024px) {
                        height: 206px;
                    }
                }


            }


        }
    }

    .author {
        display: flex;
        align-items: flex-start;
        margin-top: 30px;
        gap: 60px;

        @media (max-width: 1024px) {
            flex-direction: column;
            gap: 20px;
            margin-top: 20px;
        }

        .description {
            .desc {
                font-size: 16px;
                font-style: normal;
                font-weight: 400;
                line-height: 130%;
                font-family: var(--int);
                color: #fff;
            }

            h2 {
                font-size: 20px;
                font-style: normal;
                font-weight: 600;
                line-height: 130%;
                font-family: var(--int);
                color: #fff;
                margin: 30px 0 10px;

                @media (max-width: 1024px) {
                    margin: 20px 0 10px;
                }
            }

            h1 {
                font-size: 64px;
                font-style: normal;
                font-weight: 400;
                line-height: normal;
                font-family: var(--tka);
                color: #fff;
                margin: 0;
                display: flex;

                @media (max-width: 1024px) {
                    font-size: 36px;
                }


                img {
                    margin-left: -20px;
                    margin-top: -30px;

                    @media (max-width: 1024px) {
                        margin: -10px 0 0 -10px;
                        width: 50px;
                        height: 50px;
                    }
                }
            }
        }

        .avatar {
            background: #000;
            border: 1px solid #f00;
            padding: 10px;

            @media (max-width: 1024px) {
                width: 100%;
            }

            img {
                width: 27.865vw;
                height: 580px;
                object-fit: cover;

                @media (max-width: 1024px) {
                    width: 100%;
                    height: 469px;
                }
            }
        }
    }
}
</style>