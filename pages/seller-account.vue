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
                <div class="empty" v-if="products.length <= 0"></div>

                <div class="products__body" v-else>
                    <div class="item" v-for="item in products" :key="item.id">
                        <div class="img">
                            <img :src="pathUrl + '/api' + item.add_image[0].image" alt="">
                        </div>

                        <div class="item__info">
                            <div>
                                <span class="d-block">{{ item.name }}</span>
                                <span class="d-block">{{ item.price.toLocaleString() }} ₸</span>
                            </div>

                            <div class="item__actions">
                                <NuxtLink :to="'/edit-product/' + item.id"><img src="@/assets/img/pen.svg" alt="">
                                </NuxtLink>
                                <img src="@/assets/img/bigeye.svg" alt="">
                            </div>
                        </div>
                    </div>

                </div>
            </div>
            <div class="purchases" v-if="selectedTab == 2">
                <div class="empty" v-if="sales.length <= 0"></div>

                <div class="products__body" v-else>
                    <div class="why" v-for="item in sales" :key="item.id">
                        <div class="item">
                            <div class="img">
                                <img :src="pathUrl + '/api' + item.products.add_image[0].image" alt="">
                            </div>

                            <div class="item__info">
                                <div>
                                    <span class="d-block">{{ item.products.name }}</span>
                                    <span class="d-block">{{ item.products.price.toLocaleString() }} ₸</span>
                                    <span class="d-block designmasterpc" style="text-transform: none;">Дата продажи:
                                        {{ formatDate(item.date) }}</span>
                                    <span class="d-block designmasterpc" style="text-transform: none;">e-mail покупателя:
                                        {{ item.buyer.user.email }}</span>
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

            <TheTransactions v-if="selectedTab == 3" :transactions="transactions"></TheTransactions>

            <div class="settings" v-if="selectedTab == 4">
                <div class="avatar">
                    <label for="fileInput" class="img">
                        <div class="change__avatar">
                            <span>Изменить</span>
                        </div>
                        <img :src="photo" alt="">
                    </label>
                    <input type="file" id="fileInput" style="display: none" @change="handleFileChange">

                    <div class="buttons">
                        <button @click="editAccount()" ref="edit">сохранить</button>
                        <button @click="logOut()">выход</button>
                    </div>
                </div>

                <div class="inputs">
                    <div>
                        <label for="name">Отображаемое имя</label>
                        <input type="text" id="name" name="name" v-model="name">
                    </div>
                    <div>
                        <label for="email">Эл. почта</label>
                        <input type="email" id="email" name="email" v-model="email">
                    </div>
                    <div>
                        <label for="password">Пароль</label>
                        <input type="password" id="password" name="password" v-model="password">
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
import global from '~/mixins/global';
import axios from 'axios';
export default {
    mixins: [global],
    data() {
        return {
            selectedTab: 1,
            test: true,
            description: '',
            remainingCharacters: 10,
            description: '',
            transactions: [],
            account: [],
            avatar: null,
            name: '',
            email: '',
            pathUrl: 'https://mostshop.kz',
            description: '',
            photo: '',
            photoFile: null,
            products: [],
            sales: [],
            password: '',
        }
    },
    methods: {
        handleFileChange(event) {
            const fileInput = event.target;
            const file = fileInput.files[0];

            if (file) {
                this.displayImage(file);
                this.photoFile = file;
            }
        },
        displayImage(file) {
            const reader = new FileReader();
            reader.onload = (e) => {
                this.photo = e.target.result;
            };
            reader.readAsDataURL(file);
        },
        deleteProduct(id) {
            const path = `${this.pathUrl}/api/seller/seller-lk/delete-product/${id}`

            axios.delete(path).then(response => { this.getAccount() })

        },
        formatDate(dateString) {
            const date = new Date(dateString);
            const formattedDate = `${date.getDate().toString().padStart(2, '0')}.${(date.getMonth() + 1).toString().padStart(2, '0')}.${date.getFullYear()}`;
            return formattedDate;
        },
        getAccount() {
            const token = this.getAuthorizationCookie()
            const path = `${this.pathUrl}/api/seller/seller-lk`;
            axios.defaults.headers.common['Authorization'] = `Token ${token}`;
            axios
                .get(path)
                .then(response => {
                    this.account = response.data
                    this.name = response.data.user.first_name
                    this.email = response.data.user.email
                    this.description = response.data.description
                    this.photo = this.pathUrl + '/api' + response.data.user.photo
                    this.sales = response.data.my_sales
                    this.products = response.data.products
                    this.transactions = response.data.transactions

                })
                .catch(error => console.log(error));
        },
        editAccount() {

            const path = `${this.pathUrl}/api/seller/seller-lk/edit/`
            const csrf = this.getCSRFToken()

            const formData = new FormData();
            formData.append('user.first_name', this.name);
            formData.append('user.email', this.email);
            formData.append('user.password', this.password);
            formData.append('description', this.description);
            if (this.photoFile == null) {
                formData.append('user.photo', '');
            }
            else {
                formData.append('user.photo', this.photoFile);
            }

            axios.defaults.headers.common['X-CSRFToken'] = csrf;
            this.$refs.edit.innerHTML = 'Сохраняем'

            axios
                .put(path, formData)
                .then((res) => {
                    if (res.status == 200) {
                        this.$refs.edit.innerHTML = 'Успешно'
                        this.name = res.data.user.first_name
                        this.description = res.data.description
                        this.email = res.data.user.email
                    }
                    else {
                        this.$refs.edit.innerHTML = 'Ошибка'
                    }
                })
                .catch((error) => {
                    console.error(error);
                });
        },
    },
    mounted() {


        const accType = localStorage.getItem('accountType')
        console.log(accType)
        if (accType == 'seller-account') {
            this.getAccount()
        }
        else {
            window.location.href = '/login'
        }
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

                    a {
                        margin: 0;
                        border: 0;
                        padding: 0;
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