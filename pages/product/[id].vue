<template>
    <div v-if="product.length <= 0"></div>
    <div class="page" v-else>
        <prevPage></prevPage>

        <div class="product">
            <div class="gallery">

                <div class="main__image">
                    <img :src="mainImage" alt="">
                </div>

                <div class="image__picker">
                    <div class="picker__block" v-for="item in filteredImages">
                        <img :key="item.id" :src="item.image" @click="changeMainImage(item.image)">
                    </div>
                </div>
            </div>

            <div class="product__info">

                <div class="name__author">
                    <div class="name">
                        <h1>{{ product.name }}</h1>
                        <span>{{ product.price.toLocaleString() }} ₸</span>

                        <div class="sizes">
                            <button v-for="size in product.size.split(',')" :key="size.id" @click="select(size)">
                                <img v-show="selectedSize === size" src="@/assets/img/picked.svg" alt="">
                                {{ size }}
                            </button>
                        </div>
                    </div>
                    <div class="author">
                        <div>
                            <h2>Продавец:</h2>
                            <NuxtLink :to="'/author/' + product.seller.pk">{{ seller.first_name }}</NuxtLink>
                        </div>
                        <div>
                            <h2>Категория:</h2>
                            <span>{{ product.category.category_name }}</span>
                        </div>
                        <div>
                            <h2>Материал:</h2>
                            <span>{{ product.short_description }}</span>
                        </div>
                    </div>
                </div>

                <div class="description">
                    <h2>Описание:</h2>

                    <div v-html="product.description" class="desc"></div>

                    <div class="buttons">
                        <button @click="addToCart(productId, selectedSize)" ref="cartBtn">В корзину</button>
                        <button @click="addFav(productId, selectedSize)"><img src="@/assets/img/tofav.svg" alt=""></button>
                    </div>
                </div>

            </div>
        </div>

        <div class="similar__products">
            <h1>похожие товары</h1>

            <div class="catalog">
                <NuxtLink v-for="item in product.similar_products" :to="'/product/' + item.id" :key="item.id"
                    class="catalog__item">
                    <div class="img">
                        <div class="item__adv">
                            <div class="buttons">
                                <button @click.prevent="addFav(item.id)">
                                    <img src="@/assets/img/addcart.svg" alt="">
                                </button>
                                <button @click.prevent="addFav(item.id, item.size.split(',')[0])">
                                    <img src="@/assets/img/addfav.svg" alt="">
                                </button>
                            </div>
                        </div>
                        <img :src="item.main_image" alt="">
                    </div>
                    <p>{{ item.name }}</p>

                    <div class="text-right">
                        <span> {{ item.price.toLocaleString() }} ₸</span>
                    </div>
                </NuxtLink>
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
            sizes: [
                { id: 1, label: 'S' },
                { id: 2, label: 'M' },
                { id: 3, label: 'L' },
                { id: 4, label: 'XL' },
            ],
            selectedSize: null,
            pathUrl: "https://mostshop.kz",
            productId: this.$route.params.id,
            product: [],
            seller: [],
            category: [],
            populars: [],
            mainImage: "",
            filteredImages: [],
            description: 'Наши джинсы с рисунком лиц — это тот фокус, который добавит интереса в твой гардероб! Каждая пара придаёт тебе стиль.Комфортные в носке, рисунок не стирается при стирке. Эти джинсы — твой секрет для стильного образа <br><br> Наши джинсы с рисунком лиц — это тот фокус, который добавит интереса в твой гардероб! Каждая пара придаёт тебе стиль.Комфортные в носке, рисунок не стирается при стирке. Эти джинсы — твой секрет для стильного образ. Наши джинсы с рисунком лиц — это тот фокус, который добавит интереса в твой гардероб! Каждая пара придаёт тебе стиль.Комфортные в носке, рисунок не стирается при стирке. Эти джинсы — твой секрет для стильного образа <br> <br> Наши джинсы с рисунком лиц — это тот фокус, который добавит интереса в твой гардероб! Каждая пара придаёт тебе стиль.Комфортные в носке, рисунок не стирается при стирке. Эти джинсы — твой секрет для стильного образа. Наши джинсы с рисунком лиц — это тот фокус, который добавит интереса в твой гардероб! ',
        }
    },
    computed: {
        filteredImages() {
            return this.product.add_image;
        }
    },
    watch: {
        product: {
            handler(newVal, oldVal) {
                if (newVal && newVal.add_image) {
                    this.mainImage = newVal.add_image[0].image;
                    this.filteredImages = newVal.add_image;
                }
            },
            deep: true
        }
    },
    methods: {
        changeMainImage(newImage) {
            this.mainImage = newImage;
        },
        getProduct() {
            const path = `${this.pathUrl}/api/products/detail-product/${this.productId}`
            axios
                .get(path)
                .then(response => {
                    this.product = response.data;
                    this.seller = response.data.seller.user;
                    this.rating = response.data.seller.rating;
                    this.category = response.data.category.category_name;
                    this.count = response.data.seller.amount_products;

                    // Вызываем selectSize после загрузки данных
                    this.selectSize();
                })
                .catch(error => {
                    console.error(error);
                });
        },
        selectSize() {
            // Проверяем, есть ли размеры и selectedSize еще не установлен
            if (this.product.size && !this.selectedSize) {
                const sizes = this.product.size.split(',');
                this.selectedSize = sizes[0];
            }
        },
        select(size) {
            this.selectedSize = size === this.selectedSize ? null : size;
        },
    },
    mounted() {
        this.getProduct()

    },
}
</script>
<script setup>
useSeoMeta({
    title: 'Страница товара | Most',
    ogTitle: 'Страница товара | Most',
    description: 'Страница товара | Most',
    ogDescription: 'Страница товара | Most',
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

    .similar__products {
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

    .product {
        display: flex;
        align-items: flex-start;
        width: 100%;
        gap: 60px;
        margin-top: 30px;

        @media (max-width: 1024px) {
            flex-direction: column;
            gap: 30px;
            margin-top: 20px;
        }

        .product__info {

            .description {
                margin-top: 20px;

                .buttons {
                    margin-top: 67px;
                    display: flex;
                    gap: 30px;

                    @media (max-width: 1024px) {
                        margin-top: 30px;
                    }

                    button {
                        background: transparent;
                        border: 1px solid #f00;
                        padding: 10px 30px;

                        font-size: 20px;
                        font-style: normal;
                        font-weight: 400;
                        line-height: 130%;
                        letter-spacing: 0.2px;
                        text-transform: uppercase;
                        font-family: var(--int);
                        color: #fff;

                        &:last-child {
                            padding: 10px;
                        }
                    }
                }

                h2 {
                    font-size: 20px;
                    font-style: normal;
                    font-weight: 600;
                    line-height: 130%;
                    font-family: var(--int);
                    color: #fff;
                    margin: 0 0 10px;
                }

                .desc {
                    font-size: 16px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: 130%;
                    font-family: var(--int);
                    color: #fff;
                    max-width: 1000px;
                }
            }

            .name__author {
                display: flex;
                gap: 7.813vw;

                @media (max-width: 1024px) {
                    flex-direction: column;
                    gap: 30px;
                }

                .author {
                    display: flex;
                    flex-direction: column;
                    margin-top: 86px;
                    gap: 30px;

                    @media (max-width: 1024px) {
                        margin: 20px 0 0;
                    }

                    h2 {
                        font-size: 20px;
                        font-style: normal;
                        font-weight: 600;
                        line-height: 130%;
                        font-family: var(--int);
                        color: #fff;
                        margin: 0 0 10px;
                    }

                    a,
                    span {
                        font-size: 16px;
                        font-style: normal;
                        font-weight: 400;
                        line-height: 130%;
                        font-family: var(--int);
                        color: #fff;
                        margin: 0;
                    }

                    a {
                        text-decoration: underline;
                    }
                }

                .sizes {
                    display: flex;
                    flex-wrap: wrap;
                    gap: 33px;
                    margin-top: 25px;

                    @media (max-width: 1024px) {
                        gap: 28px;
                    }

                    button {
                        background: transparent;
                        position: relative;
                        border: 0;
                        padding: 10px 30px;

                        font-size: 16px;
                        font-style: normal;
                        font-weight: 400;
                        line-height: 130%;
                        font-family: var(--int);
                        color: #fff;



                        img {
                            position: absolute;
                            left: 0;
                            top: 0;
                        }
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
                    white-space: nowrap;

                    @media (max-width: 1660px) {
                        font-size: 48px;
                    }

                    @media (max-width: 1024px) {
                        font-size: 36px;
                    }
                }

                span {
                    font-size: 48px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: normal;
                    font-family: var(--int);
                    color: #fff;
                    display: block;
                    margin-top: 20px;

                    @media (max-width: 1660px) {
                        font-size: 35px;
                    }

                    @media (max-width: 1024px) {
                        font-size: 20px;
                    }
                }
            }
        }

        .gallery {
            display: flex;
            flex-direction: column;
            align-items: flex-start;

            @media (max-width: 1024px) {
                width: 100%;
            }

            .main__image {
                border: 1px solid #f00;
                background: #000;
                padding: 10px;

                @media (max-width: 1024px) {
                    width: 100%;
                }


                img {
                    width: 535px;
                    height: 580px;
                    object-fit: cover;
                    cursor: pointer;

                    @media (max-width: 1200px) {
                        width: 400px;
                    }

                    @media (max-width: 1024px) {
                        width: 100%;
                        height: 469px;
                    }
                }
            }

            .image__picker {
                margin-top: 20px;
                display: flex;
                flex-wrap: wrap;
                gap: 17px;

                @media (max-width: 1400px) {
                    justify-content: center;
                }

                @media (max-width: 1024px) {
                    width: 100%;
                    justify-content: flex-start;
                    flex-wrap: nowrap;
                }

                .picker__block {
                    border: 1px solid #f00;
                    background: #000;
                    padding: 5px;

                    @media (max-width: 1024px) {
                        width: 25%;
                    }

                    img {
                        width: 114.509px;
                        height: 90px;
                        object-fit: cover;
                        cursor: pointer;

                        @media (max-width: 1024px) {
                            width: 100%;
                            height: 59px;
                        }
                    }
                }
            }
        }
    }
}
</style>