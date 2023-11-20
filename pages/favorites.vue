<template>
    <div class="page">
        <div class="text-center title">
            <img src="@/assets/img/titlecover.png" class="cover" alt="">
            <h1>избранное</h1>
        </div>
        <div class="empty" v-if="!test">
            <h1>а тут пусто</h1>

            <NuxtLink to="/catalog">
                <img src="@/assets/img/defaultbg.svg" class="bg" alt="">
                <span>в каталог</span>
                <img src="@/assets/img/next.svg">
            </NuxtLink>
        </div>
        <div v-else>
            <div class="catalog__body">
                <div class="catalog">
                    <NuxtLink v-for="item in favs" :to="'/product/' + item.id" :key="item.id" class="catalog__item">
                        <div class="img">
                            <div class="item__adv">
                                <div class="buttons">
                                    <button @click.prevent="addFav(item.product.id, item.size.split(',')[0])">
                                        <img src="@/assets/img/addcart.svg" alt="">
                                    </button>
                                    <button @click.prevent="addFav(item.product.id, item.size.split(',')[0])">
                                        <img src="@/assets/img/addedfav.svg" alt="">
                                    </button>
                                </div>
                            </div>
                            <img :src="item.product.add_image[0].image" alt="">
                        </div>
                        <p>{{ item.product.name }}</p>

                        <div class="text-right">
                            <span> {{ item.product.price.toLocaleString() }} ₸</span>
                        </div>
                    </NuxtLink>
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
            test: true,
            favs: [],
        }
    },
    methods: {
        getFavs() {
            const token = this.getAuthorizationCookie()
            const path = `${this.pathUrl}/api/buyer/all-product-favourites`;
            axios.defaults.headers.common['Authorization'] = `Token ${token}`;

            axios
                .get(path)
                .then(response => {
                    this.favs = response.data
                })
                .catch(error => {
                    console.error(error)
                })
        },
    },
    mounted() {
        this.getFavs()
    }
}
</script>
<script setup>
useSeoMeta({
    title: 'Избранное | Most',
    ogTitle: 'Избранное | Most',
    description: 'Избранное | Most',
    ogDescription: 'Избранное | Most',
})
</script>
<style lang="scss" scoped>
.page {
    padding: 125px 0 123px;

    @media (max-width: 1024px) {
        padding: 125px 0 50px;
    }

    .empty {
        margin-top: 120px;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        gap: 150px;

        h1 {
            font-size: 40px;
            font-style: normal;
            font-weight: 400;
            line-height: 130%;
            font-family: var(--tka);
            color: #fff;
            margin: 0;
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

            .bg {
                position: absolute;
                left: -20px;
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

    .catalog__body {
        padding: 0 125px;

        @media (max-width: 1600px) {
            padding: 0 50px;
        }

        @media (max-width: 1024px) {
            padding: 0 20px;
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

                        button {
                            background: transparent;
                            border: 0;
                        }

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

    .title {
        position: relative;

        .cover {
            position: absolute;
            bottom: -25px;
            left: 0;
            z-index: 1;

            @media (max-width: 1024px) {
                display: none;
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

            @media (max-width: 1024px) {
                font-size: 36px;
            }
        }
    }
}
</style>