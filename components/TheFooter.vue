<template>
    <footer v-if="!hideFooterOnPages.includes($route.name)">
        <div class="footerlogo">
            <img src="@/assets/img/footerlogo.svg" class="img-fluid" alt="">
        </div>

        <div class="links">
            <div class="links__row">
                <div class="link">
                    <NuxtLink to="/catalog">КАТАЛОГ</NuxtLink>
                    <a href="/#newest">НОВИНКИ</a>
                </div>
                <div class="link">
                    <a href="/#populars">Популярное</a>
                    <NuxtLink to="/about">О Нас</NuxtLink>
                </div>
                <div class="link">
                    <a href="/#faq">Вопросы?</a>
                    <NuxtLink to="/seller-account">аккаунт</NuxtLink>
                </div>
                <div class="link">
                    <NuxtLink to="/polytics">политика конфиденциальности</NuxtLink>
                    <NuxtLink to="/terms">пользовательское соглашение</NuxtLink>
                </div>
            </div>

            <div class="copyright">
                <div>
                    <small>г. Алматы, пр-кт Республики 13, Почтовый индекс A15X3C5 (050013), +7 775 816 82 48, БИН
                        210840016943</small>
                    <small>Почта поддержки : support@most.kz</small>
                </div>
                <small>2023©most.kz </small>
            </div>
        </div>
    </footer>
</template>
<script>
export default {
    data() {
        return {
            hideFooterOnPages: ['login', 'register'],
        }
    }
}
</script>
<style lang="scss" scoped>
footer {
    width: 100%;
    border-top: 1px solid #fff;
    border-bottom: 1px solid #fff;
    display: flex;
    gap: 50px;
    align-items: flex-start;

    @media (max-width: 1300px) {
        gap: 30px;
        flex-direction: column;
    }

    @media (max-width: 1024px) {
        border: 0;
        padding: 0 20px;
    }

    .links {
        padding: 50px 0 40px;

        @media (max-width: 1024px) {
            padding: 0 20px 17px;
            width: 100%;
            padding: 0;
        }



        .copyright {
            display: flex;
            gap: 5.208vw;
            margin-top: 30px;

            @media (max-width: 1600px) {
                flex-direction: column;
                gap: 10px;
            }

            @media (max-width: 1024px) {
                margin-top: 20px;
            }

            small {
                font-size: 16px;
                font-style: normal;
                font-weight: 400;
                line-height: 130%;
                font-family: var(--int);
                color: #9B9B9B;

                @media (max-width: 1024px) {
                    font-size: 12px;
                }
            }

            div {
                display: flex;
                flex-direction: column;
                gap: 5px;
            }
        }

        .links__row {
            display: flex;
            gap: 6.094vw;

            @media (max-width: 1600px) {
                gap: 50px;
            }

            @media (max-width: 1300px) {
                gap: 30px;
            }

            @media (max-width: 1024px) {
                flex-direction: column;
                gap: 20px;
                padding: 0 0 30px;
                border-bottom: 1px solid #fff;
            }

            .link {
                display: flex;
                flex-direction: column;
                gap: 30px;

                @media (max-width: 1024px) {
                    gap: 20px;
                }

                a {
                    font-size: 20px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: normal;
                    text-transform: uppercase;
                    font-family: var(--int);
                    color: #fff;
                    text-decoration: none;

                    @media (max-width: 1600px) {
                        font-size: 16px;
                    }
                }
            }
        }
    }

    .footerlogo {
        border-right: 1px solid #fff;

        @media (max-width: 1300px) {
            border-right: 0;
            border-bottom: 1px solid #fff;
            border-top: 1px solid #fff;
            width: 100%;
            text-align: center;
        }

        img {
            margin: 61px 44px 64px 6.302vw;

            @media (max-width: 1600px) {
                margin: 78px 44px 64px 50px;
            }

            @media (max-width: 1300px) {
                margin: 61px 20px 64px 20px
            }

            @media (max-width: 1024px) {
                margin: 12px 0;
            }
        }
    }
}
</style>