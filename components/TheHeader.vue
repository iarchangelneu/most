<template>
    <header v-if="!hideHeaderOnPages.includes($route.name)">
        <div class="burg">
            <input id="menu__toggle" class="d-none" type="checkbox" />
            <label class="menu__btn" for="menu__toggle" @click="menuOpen = !menuOpen">
                <span></span>
            </label>
        </div>
        <NuxtLink to="/" class="hlogo">
            <img src="@/assets/img/headerlogo.svg" alt="">
        </NuxtLink>

        <NuxtLink to="/register" class="reg" v-if="accountType == ''">
            ВХОД / РЕГИСТРАЦИЯ
        </NuxtLink>
        <div class="options" v-else>
            <NuxtLink to="/withdrawal" class="cash">
                <img src="@/assets/img/cash.svg" alt="">
                <span>{{ userBalance == null ? '0 ₸' : userBalance.toLocaleString()
                    + ' ₸' }} </span>
            </NuxtLink>

            <div class="cart" @click.stop="toggleCart()" v-if="accountType == 'buyer'">
                <img src="@/assets/img/cart.svg" alt="">
                <div class="cart__counter" v-if="cartLength">
                    <span>{{ cartArray.length }}</span>
                </div>
            </div>

            <div class="favorites" @click.stop="toggleFavorites()" v-if="accountType == 'buyer'">
                <img src="@/assets/img/fav.svg" alt="">
                <img src="@/assets/img/favc.svg" alt="" v-if="favsLength" class="fav__checked">
            </div>

            <NuxtLink :to="this.accountUrl">
                <img src="@/assets/img/acc.svg" alt="">
            </NuxtLink>
        </div>



        <div class="Menu" :class="{ menuOpen: menuOpen }">
            <div class="menu__options">
                <div class="options" v-if="accountType !== ''">
                    <NuxtLink to="/withdrawal" class="cash">
                        <img src="@/assets/img/cash.svg" alt="">
                        <span>{{ userBalance == null ? '0 ₸' : userBalance.toLocaleString()
                            + ' ₸' }} </span>
                    </NuxtLink>
                    <NuxtLink :to="this.accountUrl">
                        <img src="@/assets/img/acc.svg" alt="">
                    </NuxtLink>
                </div>
                <div class="options" v-if="accountType == 'buyer'">
                    <div class="cart">
                        <img src="@/assets/img/cart.svg" alt="">
                        <div class="cart__counter">
                            <span>{{ cartArray.length }}</span>
                        </div>
                    </div>

                    <div class="favorites">
                        <img src="@/assets/img/fav.svg" alt="">
                        <img src="@/assets/img/favc.svg" alt="" class="fav__checked">
                    </div>
                </div>
                <NuxtLink to="/register" class="reg mob" v-if="accountType == ''">
                    ВХОД / РЕГИСТРАЦИЯ
                </NuxtLink>
            </div>
            <ul class="Menu-list" data-offset="10">
                <NuxtLink to="/catalog" class="Menu-list-item" data-offset="20" ref="menuItem" @mousemove="handleMouseMove">
                    КАТАЛОГ
                    <span class="Mask"><span>КАТАЛОГ</span></span>
                    <span class="Mask"><span>КАТАЛОГ</span></span>
                </NuxtLink>
                <NuxtLink to="/about" class="Menu-list-item" data-offset="20" ref="menuItem" @mousemove="handleMouseMove">
                    О НАС
                    <span class="Mask"><span>О НАС</span></span>
                    <span class="Mask"><span>О НАС</span></span>
                </NuxtLink>
                <a href="/populars" class="Menu-list-item" data-offset="20" ref="menuItem" @mousemove="handleMouseMove">
                    ПОПУЛЯРНОЕ
                    <span class="Mask"><span>ПОПУЛЯРНОЕ</span></span>
                    <span class="Mask"><span>ПОПУЛЯРНОЕ</span></span>
                </a>
                <a href="/faq" class="Menu-list-item" data-offset="20" ref="menuItem" @mousemove="handleMouseMove">
                    ВОПРОСЫ?
                    <span class="Mask"><span>ВОПРОСЫ?</span></span>
                    <span class="Mask"><span>ВОПРОСЫ?</span></span>
                </a>
                <!-- Add other menu items here -->
            </ul>
        </div>
        <div class="cart__menu" @click="stopPropagation" :class="{ activeMenu: cart }">

            <div class="cart__header">
                <div class="name">
                    <h2>Корзина</h2>
                    <span>({{ cartArray.length }})</span>
                </div>

                <img src="@/assets/img/closecart.svg" @click.stop="toggleCart()" alt="">
            </div>
            <div class="empty" v-if="cartArray.length <= 0">
                <div class="text-center">
                    <h1>Хэй, тут ничего. Оформим покупку?</h1>
                </div>
                <div class="cart__footer">
                    <NuxtLink to="/catalog">
                        <img src="@/assets/img/defaultbg.svg" class="bg" alt="">
                        <span>В каталог</span>
                        <img src="@/assets/img/next.svg">
                    </NuxtLink>
                </div>
            </div>
            <div v-else>
                <div class="cart__body">

                    <div class="cart__item" v-for="item in cartArray" :key="item.id">
                        <div class="img">
                            <img :src="pathUrl + '/api' + item.products.add_image[0].image" alt="">
                        </div>
                        <div class="item__info">
                            <div class="name">
                                <h3>{{ item.products.name }}</h3>
                                <span>{{ item.products.price.toLocaleString() }} ₸</span>
                            </div>
                            <small>{{ item.size }}</small>
                        </div>
                    </div>
                </div>

                <div class="cart__footer">
                    <NuxtLink to="/cart">
                        <img src="@/assets/img/defaultbg.svg" class="bg" alt="">
                        <span>ОФОРМИТЬ</span>
                        <img src="@/assets/img/next.svg">
                    </NuxtLink>
                </div>
            </div>
        </div>

        <div class="cart__menu" @click="stopPropagation" :class="{ activeMenu: favorites }">

            <div class="cart__header">
                <div class="name">
                    <h2>избранное</h2>
                    <span>({{ favs.length }})</span>
                </div>

                <img src="@/assets/img/closecart.svg" @click.stop="toggleFavorites()" alt="">
            </div>
            <div class="empty" v-if="favs.length <= 0">
                <div class="text-center">
                    <h1>а тут пусто</h1>
                </div>
                <div class="cart__footer">
                    <NuxtLink to="/catalog">
                        <img src="@/assets/img/defaultbg.svg" class="bg" alt="">
                        <span>В каталог</span>
                        <img src="@/assets/img/next.svg">
                    </NuxtLink>
                </div>
            </div>
            <div v-else>
                <div class="cart__body">

                    <div class="cart__item" v-for="item in favs" :key="item.id">
                        <div class="img">
                            <img :src="item.product.add_image[0].image" alt="">
                        </div>
                        <div class="item__info">
                            <div class="name">
                                <h3>{{ item.product.name }}</h3>
                                <span>{{ item.product.price.toLocaleString() }} ₸</span>
                            </div>
                            <div class="cart__select">
                                <small>{{ item.size }}</small>
                                <img src="@/assets/img/addcart.svg" @click="addToCart(item.product.id, item.size)"
                                    style="cursor: pointer;" alt="">
                            </div>
                        </div>
                    </div>

                </div>

                <div class="cart__footer">
                    <NuxtLink to="/favorites">
                        <img src="@/assets/img/defaultbg.svg" class="bg" alt="">
                        <span>все избранные</span>
                        <img src="@/assets/img/next.svg">
                    </NuxtLink>
                </div>
            </div>

        </div>
    </header>
</template>
<script>
import global from '~/mixins/global';
import axios from 'axios'
export default {
    mixins: [global],
    data() {
        return {
            menuOpen: false,
            cart: false,
            favorites: false,
            test: true,
            test2: true,
            hideHeaderOnPages: ['login', 'register'],
            pathUrl: 'https://mostshop.kz',
            cartArray: [],
            favs: [],
            cartLength: false,
            favsLength: false,
            userBalance: null,
            accountType: '',
        }
    },
    mounted() {
        this.$nextTick(() => {
            this.$menu = this.$refs.menuItem.parentElement;
            this.$item = this.$refs.menuItem;
            this.w = window.innerWidth;
            this.h = window.innerHeight;

            window.addEventListener('mousemove', this.handleMouseMove);
        });

        const accType = localStorage.getItem('accountType')
        if (accType == 'buyer-account') {
            this.getBuyer()
            this.getCart()
            this.getFavs()
            this.accountType = 'buyer'
            setInterval(() => {
                if (this.cartArray.length > 0) {
                    this.cartLength = true
                }
                else {
                    this.cartLength = false
                }
                if (this.favs.length > 0) {
                    this.favsLength = true
                }
                else {
                    this.favsLength = false
                }
            }, 1);
        }
        else if (accType == 'seller-account') {
            this.getSeller()
            this.accountType = 'seller'
        }
        else {
            console.log('not authorized')
        }
    },
    beforeDestroy() {
        window.removeEventListener('mousemove', this.handleMouseMove);
    },
    methods: {
        getCart() {
            const token = this.getAuthorizationCookie()
            const path = `${this.pathUrl}/api/buyer/all-product-basket`;
            axios.defaults.headers.common['Authorization'] = `Token ${token}`;

            axios
                .get(path)
                .then(response => {
                    this.cartArray = response.data
                })
                .catch(error => {
                    console.error(error)
                })
        },
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
        getBuyer() {
            const token = this.getAuthorizationCookie()
            const path = `${this.pathUrl}/api/buyer/buyer-lk`;
            axios.defaults.headers.common['Authorization'] = `Token ${token}`;
            axios
                .get(path)
                .then(response => {
                    this.userBalance = response.data.user.balance

                })
                .catch(error => console.log(error));
        },
        getSeller() {
            const token = this.getAuthorizationCookie()
            const path = `${this.pathUrl}/api/seller/seller-lk`;
            axios.defaults.headers.common['Authorization'] = `Token ${token}`;
            axios
                .get(path)
                .then(response => {
                    this.userBalance = response.data.user.balance

                })
                .catch(error => console.log(error));
        },
        toggleCart() {
            this.cart = !this.cart;
            this.getCart()
            if (this.cart) {
                document.addEventListener('click', this.closeCart);
            } else {
                document.removeEventListener('click', this.closeCart);
            }
        },
        closeCart() {
            this.cart = false;
            document.removeEventListener('click', this.closeCart);
        },
        toggleFavorites() {
            this.favorites = !this.favorites;
            this.getFavs()
            if (this.favorites) {
                document.addEventListener('click', this.closeFavorites);
            } else {
                document.removeEventListener('click', this.closeFavorites);
            }
        },
        closeFavorites() {
            this.favorites = false;
            document.removeEventListener('click', this.closeFavorites);
        },
        stopPropagation(event) {
            event.stopPropagation();
        },
        handleMouseMove(e) {
            const offsetX = 0.5 - e.pageX / this.w;
            const offsetY = 0.5 - e.pageY / this.h;
            const dy = e.pageY - this.h / 2;
            const dx = e.pageX - this.w / 2;
            const theta = Math.atan2(dy, dx);
            let angle = (theta * 180) / Math.PI - 90;

            if (angle < 0) {
                angle += 360;
            }

            const offsetPoster = this.$menu.getAttribute('data-offset');
            const transformPoster = `translate3d(0, ${-offsetX * offsetPoster}px, 0) rotateX(${-offsetY * offsetPoster}deg) rotateY(${offsetX * (offsetPoster * 2)}deg)`;

            this.$menu.style.transform = transformPoster;

            const offsetLayer = this.$item.getAttribute('data-offset') || 0;
            const transformLayer = `translate3d(${offsetX * offsetLayer}px, ${offsetY * offsetLayer}px, 20px)`;

            this.$item.style.transform = transformLayer;
        },
    },
}
</script>
<style lang="scss" scoped>
.activeMenu {
    right: 0 !important;
}

.cart__menu {
    position: fixed;
    right: -3000px;
    top: 0;
    height: 100vh;
    width: 513px;
    padding: 36px 40px;
    background: #480000;
    border: 1px solid #f00;
    z-index: 10001;
    transition: all .3s ease;

    @media (max-width: 1024px) {
        width: 100%;
        padding: 20px;
    }

    .empty {
        height: 100%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;

        h1 {
            font-size: 40px;
            font-style: normal;
            font-weight: 400;
            line-height: 130%;
            font-family: var(--tka);
            color: #fff;
            margin: 0;
            max-width: 320px;

            @media (max-width: 1024px) {
                font-size: 25px;
            }
        }
    }

    .cart__footer {
        display: flex;
        justify-content: center;
        margin-top: 100px;

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

    .cart__body {
        display: flex;
        flex-direction: column;
        gap: 30px;
        margin: 30px 0 0;
        max-height: 486px;

        overflow-y: auto;

        .cart__item {
            display: flex;
            gap: 20px;
            align-items: flex-start;

            .img {
                background: #000;
                border: 1px solid #f00;
                padding: 10px;

                img {
                    width: 120px;
                    height: 120px;
                    object-fit: cover;

                    @media (max-width: 1024px) {
                        width: 80px;
                        height: 80px;
                    }
                }
            }

            .item__info {
                display: flex;
                flex-direction: column;
                height: 142px;
                justify-content: space-between;
                align-items: flex-start;

                @media (max-width: 1024px) {
                    height: 102px;
                }

                .cart__select {
                    display: flex;
                    align-items: center;
                    gap: 35px;
                    margin-top: 41px;
                }

                h3 {
                    font-size: 20px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: normal;
                    font-family: var(--tka);
                    color: #fff;
                    margin: 0 0 10px;
                }

                span {
                    font-size: 16px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: normal;
                    font-family: var(--int);
                    color: #fff;
                }

                small {
                    font-size: 16px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: 130%;
                    font-family: var(--int);
                    color: #fff;

                    padding: 10px 30px;
                    border: 1px solid #f00;

                    @media (max-width: 1024px) {
                        padding: 10px;
                        font-size: 12px;
                    }
                }
            }
        }
    }

    .cart__header {
        display: flex;
        justify-content: space-between;
        align-items: center;

        img {
            cursor: pointer;
        }

        .name {
            display: flex;
            gap: 5px;
            align-items: flex-start;

            h2 {
                font-size: 32px;
                font-style: normal;
                font-weight: 400;
                line-height: normal;
                font-family: var(--tka);
                color: #fff;
                margin: 0;
            }

            span {
                display: block;
                font-size: 20px;
                font-style: normal;
                font-weight: 400;
                line-height: normal;
                font-family: var(--tka);
                color: #fff;
            }
        }
    }
}

header {
    width: 100%;
    position: fixed;
    z-index: 100;
    background: #1E1E1E;
    padding: 22px 100px 14px;
    display: flex;
    justify-content: space-between;

    $perspective: 60rem;
    $font-size: 4.25rem;
    $split-position: 49%;
    $split-thickness: 4px;
    $split-color: #FF0000;

    @media (max-width: 1600px) {
        padding: 22px 50px 14px;
    }

    @media (max-width: 1024px) {
        flex-direction: row-reverse;
        padding: 40px 20px 17px;
    }

    .menuOpen {
        transform: translateY(0) !important;
    }

    .Menu {
        position: fixed;
        left: 0;
        background: #1E1E1E;
        width: 100vw;
        height: 100vh;
        transform: translateY(-1000px);
        transition: all .3s ease;

        .menu__options {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 32px;
            justify-content: center;
            margin-bottom: 40px;

            @media (max-width: 1024px) {
                margin-top: 50px;
            }

            .options {
                display: flex;
                align-items: center;
                gap: 27px;

                .favorites {
                    margin-left: 18px;
                    cursor: pointer;
                    position: relative;

                    .fav__checked {
                        position: absolute;
                        top: 0;
                        right: 0;
                    }
                }

                .cart {
                    position: relative;
                    cursor: pointer;

                    .cart__counter {
                        position: absolute;
                        top: 0;
                        right: -50%;
                        border-radius: 100px/50px;
                        width: 36px;
                        height: 17px;
                        border: 1px solid #fff;
                        text-align: center;
                        display: flex;
                        flex-direction: column;
                        justify-content: center;
                        align-items: center;

                        span {
                            text-align: center;
                            font-size: 16px;
                            font-style: normal;
                            font-weight: 500;
                            line-height: normal;
                            text-transform: uppercase;
                            font-family: var(--int);
                            color: #F00;
                            display: block;
                        }
                    }
                }

                .cash {
                    display: flex;
                    gap: 10px;
                    align-items: center;
                    text-decoration: none;

                    span {
                        font-size: 20px;
                        font-style: normal;
                        font-weight: 400;
                        line-height: normal;
                        text-transform: uppercase;
                        font-family: var(--int);
                        color: #fff;
                    }
                }
            }
        }
    }

    .Menu-list {
        font-size: $font-size;
        line-height: 1.2;
        text-transform: uppercase;
        font-family: var(--tka);
        text-align: center;
        display: flex;
        flex-direction: column;
        padding: 0;
        align-items: center;
        transform: rotateX(-10deg) rotateY(20deg); // overwritten by JS
    }

    // === Menu item =====
    .Menu-list-item {
        position: relative;
        color: transparent;
        cursor: pointer;

        // === Split Line =====
        &::before {
            content: '';
            display: block;
            position: absolute;
            top: $split-position;
            left: -10%;
            right: -10%;
            height: $split-thickness;
            border-radius: $split-thickness;
            margin-top: -($split-thickness / 2);
            background: $split-color;
            transform: scale(0);
            transition: transform .8s cubic-bezier(.16, 1.08, .38, .98);
            z-index: 1;
        }
    }

    // === Top/bottom mask =====
    .Mask {
        display: block;
        position: absolute;
        overflow: hidden;
        color: $split-color;
        top: 0;
        height: $split-position;
        transition: all .8s cubic-bezier(.16, 1.08, .38, .98);

        span {
            display: block;
        }
    }

    // === Bottom mask specific =====
    .Mask+.Mask {
        top: $split-position - 0.1;
        height: 100 - $split-position + 0.1;

        span {
            transform: translateY(-$split-position);
        }
    }

    // === Where the fun stuff happens =====
    .Menu-list-item:hover,
    .Menu-list-item:active {
        .Mask {
            color: #FFF;
            transform: skewX(12deg) translateX(5px);
        }

        .Mask+.Mask {
            transform: skewX(12deg) translateX(-5px);
        }

        &::before {
            transform: scale(1);
        }
    }

    .burg {
        position: relative;

    }

    .reg {
        font-size: 36px;
        font-style: normal;
        font-weight: 400;
        line-height: normal;
        text-transform: uppercase;
        font-family: var(--tka);
        color: #fff;
        text-decoration: none;

        @media (max-width: 1024px) {
            display: none;
        }
    }

    .mob {
        @media (max-width: 1024px) {
            display: block;
        }
    }

    .hlogo {
        margin-left: 370px;

        @media (max-width: 1300px) {
            margin-left: 250px;
        }

        @media (max-width: 1024px) {
            margin: 0;
        }
    }

    .options {
        display: flex;
        align-items: center;
        gap: 27px;

        @media (max-width: 1024px) {
            display: none;
        }

        .favorites {
            margin-left: 18px;
            cursor: pointer;
            position: relative;

            .fav__checked {
                position: absolute;
                top: 0;
                right: 0;
            }
        }

        .cart {
            position: relative;
            cursor: pointer;

            .cart__counter {
                position: absolute;
                top: 0;
                right: -50%;
                border-radius: 100px/50px;
                width: 36px;
                height: 17px;
                border: 1px solid #fff;
                text-align: center;
                display: flex;
                flex-direction: column;
                justify-content: center;
                align-items: center;

                span {
                    text-align: center;
                    font-size: 16px;
                    font-style: normal;
                    font-weight: 500;
                    line-height: normal;
                    text-transform: uppercase;
                    font-family: var(--int);
                    color: #F00;
                    display: block;
                }
            }
        }

        .cash {
            display: flex;
            gap: 10px;
            align-items: center;
            text-decoration: none;

            span {
                font-size: 20px;
                font-style: normal;
                font-weight: 400;
                line-height: normal;
                text-transform: uppercase;
                font-family: var(--int);
                color: #fff;
            }
        }
    }
}



#menu__toggle {
    opacity: 0;
}

.menu__btn {
    margin-top: 10px;
    display: flex;
    /* используем flex для центрирования содержимого */
    align-items: center;
    /* центрируем содержимое кнопки */
    width: 35px;
    height: 20px;
    cursor: pointer;
    z-index: 1000;
    color: #fff;
    position: relative;
    transform: rotate(180deg);
}

.menu__btn>span {
    display: block;
    position: absolute;
    width: 100%;
    height: 2px;
    background-color: #fff;
}

.menu__btn>span::before,
.menu__btn>span::after {
    display: block;
    position: absolute;
    width: 100%;
    height: 2px;
    background-color: #fff;
}

.menu__btn>span::before {
    content: '';
    top: -8px;
}

.menu__btn>span::after {
    content: '';
    top: 8px;
}

#menu__toggle:checked~.menu__btn>span {
    transform: rotate(45deg);
    background-color: #fff;
    border-radius: 10px;

}

#menu__toggle:checked~.menu__btn>span::before {
    top: 0;
    transform: rotate(0);
    background-color: #fff;
    border-radius: 10px;

}

#menu__toggle:checked~.menu__btn>span::after {
    top: 0;
    transform: rotate(90deg);
    background-color: #fff;
    border-radius: 10px;
}

#menu__toggle:checked~.menu__box {
    visibility: visible;
    top: 0;
}

.menu__btn>span,
.menu__btn>span::before,
.menu__btn>span::after {
    transition-duration: .25s;
}
</style>