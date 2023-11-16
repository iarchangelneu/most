<template>
    <div>
        <div class="text-center title">
            <img src="@/assets/img/titlecover.png" class="cover" alt="">
            <h1>каталог</h1>
        </div>
        <div class="page">
            <div class="filters">
                <div class="filters__body">
                    <div class="input-group">
                        <input type="text" class="form-control" placeholder="Искать..." aria-label="search"
                            aria-describedby="basic-addon1">
                        <div class="input-group-prepend">
                            <span class="input-group-text" id="basic-addon1"><img src="@/assets/img/search.svg"
                                    alt=""></span>
                        </div>
                    </div>

                    <div class="filters__buttons">
                        <button @click.stop="toggleFilter">ФИЛЬТР</button>
                        <button @click.stop="toggleSort">СОРТИРОВАТЬ</button>

                        <div class="sort__body" @click="stopPropagation" :class="{ active: sort }">
                            <span @click="selectedSort = 1, closeSort()" :class="{ spanActive: selectedSort == 1 }">Сначала
                                дешевле</span>
                            <span @click="selectedSort = 2, closeSort()" :class="{ spanActive: selectedSort == 2 }">Сначала
                                дороже</span>
                            <span @click="selectedSort = 3, closeSort()"
                                :class="{ spanActive: selectedSort == 3 }">Популярное</span>
                            <span @click="selectedSort = 4, closeSort()"
                                :class="{ spanActive: selectedSort == 4 }">Новинки</span>
                        </div>

                        <div class="filter__body" @click="stopPropagation" :class="{ active: filter }">
                            <div class="item">
                                <h2>предмет:</h2>

                                <div class="items__check">
                                    <label class="custom-checkbox">
                                        <input type="checkbox">
                                        <p class="checkbox-text m-0">Все</p>
                                    </label>
                                    <label class="custom-checkbox">
                                        <input type="checkbox">
                                        <p class="checkbox-text m-0">Верх</p>
                                    </label>
                                    <label class="custom-checkbox">
                                        <input type="checkbox">
                                        <p class="checkbox-text m-0">Низ</p>
                                    </label>
                                    <label class="custom-checkbox">
                                        <input type="checkbox">
                                        <p class="checkbox-text m-0">Аксессуары</p>
                                    </label>
                                    <label class="custom-checkbox">
                                        <input type="checkbox">
                                        <p class="checkbox-text m-0">Головные уборы</p>
                                    </label>
                                    <label class="custom-checkbox">
                                        <input type="checkbox">
                                        <p class="checkbox-text m-0">Обувь</p>
                                    </label>
                                    <label class="custom-checkbox">
                                        <input type="checkbox">
                                        <p class="checkbox-text m-0">Костюм</p>
                                    </label>
                                </div>
                            </div>
                            <div class="price">
                                <h2>Цена:</h2>
                                <div class="price__input">
                                    <div class="input-group">
                                        <input type="number" class="form-control" placeholder="От" aria-label="from"
                                            aria-describedby="basic-addon1">
                                        <div class="input-group-prepend">
                                            <span class="input-group-text" id="basic-addon1">₸</span>
                                        </div>
                                    </div>

                                    <img src="@/assets/img/line.svg" alt="">

                                    <div class="input-group">
                                        <input type="number" class="form-control" placeholder="До" aria-label="to"
                                            aria-describedby="basic-addon1">
                                        <div class="input-group-prepend">
                                            <span class="input-group-text" id="basic-addon1">₸</span>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>


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


            <div class="showmore">
                <img src="@/assets/img/showmore.svg" class="shmr" alt="">
                <button ref="showmore">Показать<br> еще</button>
                <img src="@/assets/img/showmorearr.svg" alt="">
            </div>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            filter: false,
            sort: false,
            selectedSort: 0,
        }
    },
    methods: {
        toggleFilter() {
            this.filter = !this.filter;

            if (this.filter) {
                document.addEventListener('click', this.closeFilter);
            } else {
                document.removeEventListener('click', this.closeFilter);
            }
        },
        closeFilter() {
            this.filter = false;
            document.removeEventListener('click', this.closeFilter);
        },
        toggleSort() {
            this.sort = !this.sort;
            if (this.sort) {
                document.addEventListener('click', this.closeSort);
            } else {
                document.removeEventListener('click', this.closeSort);
            }
        },
        closeSort() {
            this.sort = false;
            document.removeEventListener('click', this.closeSort);
        },
        stopPropagation(event) {
            event.stopPropagation();
        },
    }
}
</script>
<script setup>
useSeoMeta({
    title: 'Каталог | Most',
    ogTitle: 'Каталог | Most',
    description: 'Каталог | Most',
    ogDescription: 'Каталог | Most',
})
</script>
<style lang="scss" scoped>
.page {
    padding: 0 125px 100px;

    @media (max-width: 1600px) {
        padding: 0 50px 100px;
    }

    @media (max-width: 1024px) {
        padding: 0 20px 50px;
    }

    .showmore {
        display: flex;
        justify-content: center;
        align-items: center;
        position: relative;
        margin-top: 100px;
        cursor: pointer;

        .shmr {
            position: absolute;
        }

        button {
            background: transparent;
            border: 0;
            font-size: 20px;
            font-style: normal;
            font-weight: 400;
            line-height: 130%;
            /* 26px */
            text-transform: uppercase;
            font-family: var(--int);
            color: #fff;
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

    .filters {
        margin-top: 30px;
        display: flex;
        justify-content: center;

        .filters__body {

            @media (max-width: 1024px) {
                width: 100%;
            }

            .input-group {
                flex-wrap: nowrap;
            }

            .filters__buttons {
                display: flex;
                justify-content: center;
                gap: 20px;
                margin: 20px 0 0;
                position: relative;

                @media (max-width: 1024px) {
                    flex: 1;
                }

                .active {
                    transform: scale(1) !important;
                }

                .sort__body {
                    z-index: 10;
                    border: 1px solid #F00;
                    background: #480000;
                    padding: 15px 20px;
                    width: 218px;
                    transform: scale(0);
                    transition: all .3s ease;

                    display: flex;
                    flex-direction: column;
                    gap: 10px;
                    text-align: center;

                    position: absolute;
                    margin-top: 65px;

                    @media (max-width: 1024px) {
                        width: 100%;
                    }

                    .spanActive {
                        color: #F00 !important;
                    }

                    span {
                        cursor: pointer;
                        font-size: 20px;
                        font-style: normal;
                        font-weight: 400;
                        line-height: normal;
                        font-family: var(--int);
                        color: #fff;
                    }
                }

                .filter__body {
                    z-index: 10;
                    border: 1px solid #F00;
                    background: #480000;
                    padding: 15px 20px;
                    width: 531px;
                    transform: scale(0);
                    transition: all .3s ease;


                    display: flex;
                    justify-content: space-between;

                    position: absolute;
                    margin-top: 65px;

                    @media (max-width:1024px) {
                        width: 100%;
                        flex-direction: column;
                    }

                    h2 {
                        font-size: 32px;
                        font-style: normal;
                        font-weight: 400;
                        line-height: normal;
                        font-family: var(--tka);
                        color: #fff;
                        margin: 0 0 10px;
                    }

                    .item {

                        .items__check {
                            display: flex;
                            flex-direction: column;
                            gap: 20px;

                            label {
                                margin: 0;
                            }
                        }

                        p {
                            font-size: 16px;
                            font-style: normal;
                            font-weight: 400;
                            line-height: normal;
                            font-family: var(--int);
                            color: #fff;
                            margin: 0;
                        }
                    }

                    .price {
                        .price__input {
                            display: flex;
                            gap: 10px;

                            .input-group-text {
                                color: #fff;
                                font-size: 16px;
                                font-style: normal;
                                font-weight: 400;
                                line-height: normal;
                                font-family: var(--int);
                            }

                            input {
                                width: 100px;
                                color: #fff;

                                @media (max-width: 1024px) {
                                    width: 60px;
                                    height: 28px;
                                }

                                &::placeholder {
                                    color: #fff;
                                }
                            }
                        }


                    }

                }

                button {
                    border: 1px solid #F00;
                    background: transparent;
                    padding: 10px 30px;

                    font-size: 20px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: normal;
                    font-family: var(--tka);
                    color: #fff;

                    @media (max-width: 1024px) {
                        flex: 1;
                        padding: 10px 0;
                    }
                }
            }

            .input-group-text {
                background: #480000;
                border: 1px solid #F00;
                border-left: 0;
                padding: 2px 15px 1px 5px;
            }

            input {
                border: 1px solid #F00;
                background: #480000;
                border-radius: 0;
                padding: 11px 15px;
                border-right: 0;

                font-size: 20px;
                font-style: normal;
                font-weight: 400;
                line-height: normal;
                font-family: var(--int);
                color: #fff;
                box-shadow: none;
                width: 600px;

                &::placeholder {
                    color: #7C5555;
                }
            }
        }
    }
}

.title {
    padding: 100px 0 0;
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
    width: 20px;
    height: 20px;
    margin-right: 10px;
    border: 1px solid #F00;
    border-radius: 0;
    margin-bottom: 3px;
}

.custom-checkbox input[type="checkbox"]:checked+.checkbox-text:before {
    content: url('@/assets/img/check.svg');
    font-size: 15px;
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