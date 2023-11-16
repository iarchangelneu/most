<template>
    <div class="page">

        <h1>уупс, При оплате произошла ошибка</h1>
        <h1>попробуй повторить попытку позже</h1>
        <img src="@/assets/img/titlecover.png" class="cover" alt="">
        <div class="confirm">
            <NuxtLink to="/complete-order">
                <img src="@/assets/img/defaultbg.svg" class="bg" alt="">
                <span ref="complete">повторить попытку</span>
                <img src="@/assets/img/next.svg">
            </NuxtLink>
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
    title: 'Ошибка при оформлении заказа | Most',
    ogTitle: 'Ошибка при оформлении заказа | Most',
    description: 'Ошибка при оформлении заказа | Most',
    ogDescription: 'Ошибка при оформлении заказа | Most',
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
                left: 5%;

                @Media (max-width: 1024px) {
                    left: -20px;
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