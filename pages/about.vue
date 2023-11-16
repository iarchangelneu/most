<template>
    <div class="page">
        <div class="text-center title">
            <img src="@/assets/img/titlecover.png" class="cover" alt="">
            <h1>о нас</h1>
        </div>

        <div class="about__body text-center">
            <img src="@/assets/img/aboutpc.png" class="img-fluid pc" alt="">
            <img src="@/assets/img/aboutmob.png" alt="" class="img-fluid mob">
        </div>
    </div>
</template>
<script setup>
useSeoMeta({
    title: 'О нас | Most',
    ogTitle: 'О нас | Most',
    description: 'О нас | Most',
    ogDescription: 'О нас | Most',
})
</script>
<style lang="scss" scoped>
.page {
    padding: 125px 0 50px;

    .pc {
        @media (max-width: 1024px) {
            display: none;
        }
    }

    .mob {
        display: none;
        width: 100%;

        @media (max-width: 1024px) {
            display: block;
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