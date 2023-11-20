<template>
    <div class="page">

        <h1>Успех!</h1>
        <h1>Транзакция прошла успешно</h1>
        <img src="@/assets/img/titlecover.png" class="cover" alt="">
        <div class="confirm">
            <NuxtLink to="/catalog">
                <img src="@/assets/img/defaultbg.svg" class="bg" alt="">
                <span ref="complete">в каталог</span>
                <img src="@/assets/img/next.svg">
            </NuxtLink>
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
            pathUrl: 'https://mostshop.kz',
        }
    }
    ,
    methods: {
        sendRequest(reference) {
            const token = this.getAuthorizationCookie();
            const path = `${this.pathUrl}/api/money/success/${reference}`;
            axios.defaults.headers.common['Authorization'] = `Token ${token}`;
            axios
                .get(path)
                .then(response => {
                    console.log(response)
                    if (response.status == 200) {
                        //  window.location.href = '/'
                    }
                })
                .catch(error => {
                    console.log(error);
                });
        },
    },
    mounted() {
        const url = window.location.href;
        const match = url.match(/order_pay_mostshop_(\d+)/);

        if (match) {
            this.extractedValue = match[0];
            console.log(this.extractedValue);

            this.sendRequest(match[0])
        }
    },
}
</script>
<script setup>
useSeoMeta({
    title: 'Успех | Most',
    ogTitle: 'Успех | Most',
    description: 'Успех | Most',
    ogDescription: 'Успех | Most',
})
</script>
<style lang="scss" scoped>
.page {
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    gap: 30px;
    text-align: center;
    position: relative;
    padding: 125px 20px 70px;

    @media (max-width: 1024px) {
        gap: 10px;
    }

    .cover {
        position: absolute;
        top: 40%;
        z-index: 1;

        @media (max-width: 1024px) {
            display: none;
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
        z-index: 2;

        @media (max-width: 1024px) {
            font-size: 24px;
        }
    }

    .confirm {
        margin-top: 70px;
        display: flex;
        justify-content: center;

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
}
</style>