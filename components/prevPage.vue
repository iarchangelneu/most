<template>
    <div class="back">
        <button @click="goBack">
            <img src="@/assets/img/prev.svg" alt="" loading="lazy">
            <span>Назад</span>
        </button>


    </div>
</template>
<script>
export default {
    methods: {
        goBack() {
            this.prevPage = this.$nuxt.$router.go(-1);
        },
    },
}
</script>
<style lang="scss" scoped>
.back {
    button {
        border-radius: 0;
        border: 1px solid #f00;
        background: transparent;
        padding: 10px 20px;
        display: flex;
        align-items: center;
        gap: 10px;
        text-transform: uppercase;

        font-size: 16px;
        font-style: normal;
        font-weight: 400;
        line-height: 130%;
        font-family: var(--int);
        color: #fff;
    }
}
</style>