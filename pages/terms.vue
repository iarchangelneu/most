<template>
    <div class="page">
        <h1>ПОЛЬЗОВАТЕЛЬСКОЕ СОГЛАШЕНИЕ</h1>

        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Commodi unde ratione ipsum sapiente, nesciunt nobis qui
            consequuntur adipisci corrupti iste voluptate, facilis rem possimus repellat modi cumque. A, illum doloribus.
        </p>
    </div>
</template>
<script setup>
useSeoMeta({
    title: 'Пользовательское соглашение | Most',
    ogTitle: 'Пользовательское соглашение | Most',
    description: 'Пользовательское соглашение | Most',
    ogDescription: 'Пользовательское соглашение | Most',
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

    h1 {
        text-align: center;
        font-size: 64px;
        font-style: normal;
        font-weight: 400;
        line-height: normal;
        font-family: var(--tka);
        color: #fff;
        margin: 0 0 30px;

        @media (max-width: 1024px) {
            font-size: 24px;
            margin: 0 0 15px;
        }
    }

    p {
        font-size: 16px;
        font-style: normal;
        font-weight: 600;
        line-height: 140%;
        font-family: var(--int);
        color: #fff;
        margin: 0;
    }
}
</style>