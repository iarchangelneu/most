<template>
    <div class="page">
        <div class="main">
            <div class="links pc">
                <NuxtLink class="link" to='/about'>
                    <img src="@/assets/img/linkbg.svg" alt="" class="linkbg">
                    <span>подробнее о нас</span>
                    <img src="@/assets/img/linkarrow.svg" alt="">
                </NuxtLink>

                <img src="@/assets/img/main.png" class="centered img-fluid" alt="">

                <NuxtLink to="/catalog" class="link">
                    <img src="@/assets/img/linkbg.svg" class="linkbg" alt="">
                    <span>Перейти в каталог</span>
                    <img src="@/assets/img/linkarrow.svg" alt="">
                </NuxtLink>
            </div>
            <img src="@/assets/img/redline.png" class="redline img-fluid" alt="">
            <img src="@/assets/img/redlinemob.svg" class="redline redlinemob img-fluid" alt="">

            <div class="links mob">
                <NuxtLink class="link" to='/about'>
                    <img src="@/assets/img/linkbg.svg" alt="" class="linkbg">
                    <span>подробнее о нас</span>
                    <img src="@/assets/img/linkarrow.svg" alt="">
                </NuxtLink>

                <NuxtLink class="link" to="/catalog">
                    <img src="@/assets/img/linkbg.svg" alt="" class="linkbg">
                    <span>Перейти в каталог</span>
                    <img src="@/assets/img/linkarrow.svg" alt="">
                </NuxtLink>
            </div>
        </div>

        <div class="popular" ref="popularBlock">
            <div class="title">
                <h1>ПОПУЛЯРНОЕ</h1>
                <div class="covertitle" :style="{ width: popularCoverWidth }">
                    <h2>ПОПУЛЯРНОЕ</h2>
                </div>
            </div>


            <div class="catalog">
                <NuxtLink :to="'/product/' + 1" class="catalog__item">
                    <img src="@/assets/img/pop1.png" alt="">

                    <p>Джинсы «Fases»</p>

                    <div class="text-right">
                        <span> 34 555 ₸</span>
                    </div>
                </NuxtLink>
                <NuxtLink :to="'/product/' + 1" class="catalog__item">
                    <img src="@/assets/img/pop2.png" alt="">

                    <p>Кроссовки «Say Yes»</p>

                    <div class="text-right">
                        <span> 57 999 ₸</span>
                    </div>
                </NuxtLink>
                <NuxtLink :to="'/product/' + 1" class="catalog__item">
                    <img src="@/assets/img/pop3.png" alt="">

                    <p>Куртка «JO»</p>

                    <div class="text-right">
                        <span> 122 940 ₸</span>
                    </div>
                </NuxtLink>
                <NuxtLink :to="'/product/' + 1" class="catalog__item">
                    <img src="@/assets/img/pop4.png" alt="">

                    <p>Топ «KRASIVO»</p>

                    <div class="text-right">
                        <span> 31 550 ₸</span>
                    </div>
                </NuxtLink>
                <NuxtLink :to="'/product/' + 1" class="catalog__item">
                    <img src="@/assets/img/pop5.png" alt="">

                    <p>Рубашка «Art»</p>

                    <div class="text-right">
                        <span> 18 370 ₸</span>
                    </div>
                </NuxtLink>
            </div>
        </div>


        <div class="urstyle text-center">
            <img src="@/assets/img/style.png" class="style img-fluid" alt="">
            <div class="line">
                <div class="running-text">
                    <div class="text-container">
                        <div class="text-segment">FASHION</div>
                        <div class="text-segment">WITHOUT RULES</div>
                        <div class="text-segment">BE BRIGHT</div>
                        <div class="text-segment">LAUGHTER</div>
                        <div class="text-segment">HARDY</div>
                        <div class="text-segment">EXCEPT</div>
                        <div class="text-segment">SHOW ME</div>
                        <div class="text-segment">IMPROVEMENT</div>
                        <div class="text-segment">UNIQUE</div>
                        <div class="text-segment">REMEMBER</div>
                        <div class="text-segment">FOR ALL</div>
                        <div class="text-segment">REALIZE</div>
                        <div class="text-segment">SELL</div>
                        <div class="text-segment">BUILD THE MODU</div>
                        <div class="text-segment">FASHION</div>
                        <div class="text-segment">WITHOUT RULES</div>
                        <div class="text-segment">BE BRIGHT</div>
                        <div class="text-segment">LAUGHTER</div>
                        <div class="text-segment">HARDY</div>
                        <div class="text-segment">EXCEPT</div>
                        <div class="text-segment">SHOW ME</div>
                        <div class="text-segment">IMPROVEMENT</div>
                        <div class="text-segment">UNIQUE</div>
                        <div class="text-segment">REMEMBER</div>
                        <div class="text-segment">FOR ALL</div>
                        <div class="text-segment">REALIZE</div>
                        <div class="text-segment">SELL</div>
                        <div class="text-segment">BUILD THE MODU</div>
                        <div class="text-segment">FASHION</div>
                        <div class="text-segment">WITHOUT RULES</div>
                        <div class="text-segment">BE BRIGHT</div>
                        <div class="text-segment">LAUGHTER</div>
                        <div class="text-segment">HARDY</div>
                        <div class="text-segment">EXCEPT</div>
                        <div class="text-segment">SHOW ME</div>
                        <div class="text-segment">IMPROVEMENT</div>
                        <div class="text-segment">UNIQUE</div>
                        <div class="text-segment">REMEMBER</div>
                        <div class="text-segment">FOR ALL</div>
                        <div class="text-segment">REALIZE</div>
                        <div class="text-segment">SELL</div>
                        <div class="text-segment">BUILD THE MODU</div>
                        <div class="text-segment">FASHION</div>
                        <div class="text-segment">WITHOUT RULES</div>
                        <div class="text-segment">BE BRIGHT</div>
                        <div class="text-segment">LAUGHTER</div>
                        <div class="text-segment">HARDY</div>
                        <div class="text-segment">EXCEPT</div>
                        <div class="text-segment">SHOW ME</div>
                        <div class="text-segment">IMPROVEMENT</div>
                        <div class="text-segment">UNIQUE</div>
                        <div class="text-segment">REMEMBER</div>
                        <div class="text-segment">FOR ALL</div>
                        <div class="text-segment">REALIZE</div>
                        <div class="text-segment">SELL</div>
                        <div class="text-segment">BUILD THE MODU</div>
                    </div>
                </div>
            </div>
            <div class="line2">
                <div class="running-text">
                    <div class="text-container">
                        <div class="text-segment">FASHION</div>
                        <div class="text-segment">WITHOUT RULES</div>
                        <div class="text-segment">BE BRIGHT</div>
                        <div class="text-segment">LAUGHTER</div>
                        <div class="text-segment">HARDY</div>
                        <div class="text-segment">EXCEPT</div>
                        <div class="text-segment">SHOW ME</div>
                        <div class="text-segment">IMPROVEMENT</div>
                        <div class="text-segment">UNIQUE</div>
                        <div class="text-segment">REMEMBER</div>
                        <div class="text-segment">FOR ALL</div>
                        <div class="text-segment">REALIZE</div>
                        <div class="text-segment">SELL</div>
                        <div class="text-segment">BUILD THE MODU</div>
                        <div class="text-segment">FASHION</div>
                        <div class="text-segment">WITHOUT RULES</div>
                        <div class="text-segment">BE BRIGHT</div>
                        <div class="text-segment">LAUGHTER</div>
                        <div class="text-segment">HARDY</div>
                        <div class="text-segment">EXCEPT</div>
                        <div class="text-segment">SHOW ME</div>
                        <div class="text-segment">IMPROVEMENT</div>
                        <div class="text-segment">UNIQUE</div>
                        <div class="text-segment">REMEMBER</div>
                        <div class="text-segment">FOR ALL</div>
                        <div class="text-segment">REALIZE</div>
                        <div class="text-segment">SELL</div>
                        <div class="text-segment">BUILD THE MODU</div>
                        <div class="text-segment">FASHION</div>
                        <div class="text-segment">WITHOUT RULES</div>
                        <div class="text-segment">BE BRIGHT</div>
                        <div class="text-segment">LAUGHTER</div>
                        <div class="text-segment">HARDY</div>
                        <div class="text-segment">EXCEPT</div>
                        <div class="text-segment">SHOW ME</div>
                        <div class="text-segment">IMPROVEMENT</div>
                        <div class="text-segment">UNIQUE</div>
                        <div class="text-segment">REMEMBER</div>
                        <div class="text-segment">FOR ALL</div>
                        <div class="text-segment">REALIZE</div>
                        <div class="text-segment">SELL</div>
                        <div class="text-segment">BUILD THE MODU</div>
                        <div class="text-segment">FASHION</div>
                        <div class="text-segment">WITHOUT RULES</div>
                        <div class="text-segment">BE BRIGHT</div>
                        <div class="text-segment">LAUGHTER</div>
                        <div class="text-segment">HARDY</div>
                        <div class="text-segment">EXCEPT</div>
                        <div class="text-segment">SHOW ME</div>
                        <div class="text-segment">IMPROVEMENT</div>
                        <div class="text-segment">UNIQUE</div>
                        <div class="text-segment">REMEMBER</div>
                        <div class="text-segment">FOR ALL</div>
                        <div class="text-segment">REALIZE</div>
                        <div class="text-segment">SELL</div>
                        <div class="text-segment">BUILD THE MODU</div>
                    </div>
                </div>
            </div>
        </div>
        <div class="newest" ref="newestBlock">
            <div class="title">
                <h1>НОВИНКИ</h1>
                <div class="covertitle" :style="{ width: newestCoverWidth }">
                    <h2>НОВИНКИ</h2>
                </div>
            </div>

            <div class="catalog">
                <NuxtLink :to="'/product/' + 1" class="catalog__item">
                    <img src="@/assets/img/pop1.png" alt="">

                    <p>Джинсы «Fases»</p>

                    <div class="text-right">
                        <span> 34 555 ₸</span>
                    </div>
                </NuxtLink>
                <NuxtLink :to="'/product/' + 1" class="catalog__item">
                    <img src="@/assets/img/pop2.png" alt="">

                    <p>Кроссовки «Say Yes»</p>

                    <div class="text-right">
                        <span> 57 999 ₸</span>
                    </div>
                </NuxtLink>
                <NuxtLink :to="'/product/' + 1" class="catalog__item">
                    <img src="@/assets/img/pop3.png" alt="">

                    <p>Куртка «JO»</p>

                    <div class="text-right">
                        <span> 122 940 ₸</span>
                    </div>
                </NuxtLink>
                <NuxtLink :to="'/product/' + 1" class="catalog__item">
                    <img src="@/assets/img/pop4.png" alt="">

                    <p>Топ «KRASIVO»</p>

                    <div class="text-right">
                        <span> 31 550 ₸</span>
                    </div>
                </NuxtLink>
                <NuxtLink :to="'/product/' + 1" class="catalog__item">
                    <img src="@/assets/img/pop5.png" alt="">

                    <p>Рубашка «Art»</p>

                    <div class="text-right">
                        <span> 18 370 ₸</span>
                    </div>
                </NuxtLink>
            </div>
        </div>

        <div class="about" ref="aboutBlock">
            <div class="title">
                <h1>О НАС</h1>
                <div class="covertitle" :style="{ width: aboutCoverWidth }">
                    <h2>О НАС</h2>
                </div>
            </div>

            <div class="about__block">
                <img src="@/assets/img/about1.png" class="img-fluid bigimg" alt="">

                <div>
                    <p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Хэй! Давай расскажем тебе о нашем
                        маркетплейсе, где стиль
                        и креативность нашли своё уютное гнёздышко!
                        У нас не просто мода, у нас искусство самовыражения. Мы собрали воедино потрясающие находки,
                        созданные
                        настоящими художниками и дизайнерами. Здесь ты можешь не только разгуляться в шопинге, но и стать
                        звездой своей собственной модной истории.</p>

                    <p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;И это ещё не всё! Мы также открыты
                        для креативных гениев, которые сами
                        создают уникальные наряды.
                        Если у тебя есть свой собственный стиль или даже собственные дизайны, у нас есть идеальная площадка,
                        чтобы представить их миру. Присоединяйся к нашему креативному сообществу, и вместе мы сделаем этот
                        мир ещё более красочным и увлекательным. Здесь стиль — это твоя собственная история, и мы гордимся,
                        что можем помочь тебе выразить себя 🌟</p>
                </div>

                <div class="aboutBlocks">
                    <div>
                        <img src="@/assets/img/about2.png" class="img-fluid" alt="">
                        <img src="@/assets/img/about3.png" class="abt3 img-fluid" alt="">
                    </div>
                    <div>
                        <NuxtLink class="link" to='/about'>
                            <img src="@/assets/img/linkbg.svg" alt="" class="linkbg">
                            <NuxtLink to='/about'>подробнее о нас</NuxtLink>
                            <img src="@/assets/img/linkarrow.svg" alt="">
                        </NuxtLink>

                        <img src="@/assets/img/about4.png" class="img-fluid" alt="">
                    </div>
                </div>
            </div>
        </div>
        <div class="faq" ref="faqBlock">
            <div class="title">
                <h1>ВОПРОСЫ</h1>
                <div class="covertitle" :style="{ width: faqCoverWidth }">
                    <h2>ВОПРОСЫ?</h2>
                </div>
            </div>

            <div class="faq__body">
                <img src="@/assets/img/faq1.png" class="img-fluid" alt="">

                <div class="faq__right">
                    <button v-for="faq in faqs" :key="faq.id" :data-target="'#collapseExample' + faq.id"
                        aria-expanded="false" :aria-controls="'collapseExample' + faq.id" @click="toggleCollapse(faq.id)">
                        <div class="inside">
                            <span>
                                {{ faq.question }}
                            </span>
                            <img src="@/assets/img/plus.svg" :class="{ rotate: faq.isOpen }"
                                style="transition: all .3s ease;" alt="">
                        </div>

                        <div :class="{ collapse: !faq.isOpen }" style="transition:  all .3s ease;"
                            :id="'collapseExample' + faq.id">
                            <span class="mt-4 d-block trep">{{ faq.answer }}</span>
                        </div>
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            popularCoverWidth: '0%',
            newestCoverWidth: '0%',
            aboutCoverWidth: '0%',
            faqCoverWidth: '0%',
            faqs: [
                { id: 1, isOpen: false, question: 'Как я могу продать одежду на вашей платформе?', answer: 'Регистрируйтесь на платформе как продавец и размещайте товары по своим ценам' },
                { id: 2, isOpen: false, question: 'Существует ли у вас комиссия? И сколько?', answer: 'Нет, сайт не берет комиссию ни с продавца, ни с покупателя' },
                { id: 3, isOpen: false, question: 'Какова политика конфиденциальности вашего сайта?', answer: 'Нет, сайт не берет комиссию ни с продавца, ни с покупателя' },
                { id: 4, isOpen: false, question: ' У вас есть физический магазин или все продажи онлайн?', answer: 'Нет, сайт не берет комиссию ни с продавца, ни с покупателя' },
                { id: 5, isOpen: false, question: ' Какие бренды и дизайнеры представлены на вашей платформе?', answer: ' Нет, сайт не берет комиссию ни с продавца, ни с покупателя' },
            ],
        };
    },
    methods: {
        toggleCollapse(id) {
            const faq = this.faqs.find(f => f.id === id);
            faq.isOpen = !faq.isOpen;
        },
        handleScroll() {
            const refs = this.$refs;
            const positions = this.getBlockPositions(['popularBlock', 'newestBlock', 'aboutBlock', 'faqBlock']);

            ['popularCoverWidth', 'newestCoverWidth', 'aboutCoverWidth', 'faqCoverWidth']
                .forEach((coverWidthVar, index) => this.updateCoverWidth(positions[index], coverWidthVar, 1));
        },
        getBlockPositions(blocks) {
            return blocks.map(blockRef => this.$refs[blockRef].getBoundingClientRect().top);
        },
        updateCoverWidth(blockPosition, coverWidthVar, speed) {
            const isInView = blockPosition < window.innerHeight && blockPosition > 0;

            if (isInView) {
                this.animateCoverWidth(coverWidthVar, '100%', 0.01);
            } else {
                this.animateCoverWidth(coverWidthVar, '0%', 0.01);
            }
        },

        animateCoverWidth(coverWidthVar, targetWidth, speed) {
            const currentWidth = parseFloat(this[coverWidthVar]);
            const targetWidthValue = parseFloat(targetWidth);
            const step = speed * (targetWidthValue - currentWidth);

            this[coverWidthVar] = `${currentWidth + step}%`;
        },
    },
    mounted() {
        window.addEventListener('scroll', this.handleScroll);
    },

}
</script>
<script setup>
useSeoMeta({
    title: 'Главная | Most',
    ogTitle: 'Главная | Most',
    description: 'Главная | Most',
    ogDescription: 'Главная | Most',
})
</script>
<style lang="scss" scoped>
.page {
    .faq {
        margin-top: 60px;

        .faq__body {

            padding: 30px 135px 170px;
            display: flex;
            align-items: flex-start;
            gap: 84px;

            @media (max-width: 1600px) {
                padding: 30px 50px 70px;
            }

            @media (max-width: 1024px) {
                padding: 30px 20px 50px;
                flex-direction: column-reverse;
                gap: 27px;
            }

            .faq__right {
                width: 100%;
                display: flex;
                flex-direction: column;
                gap: 43px;

                .rotate {
                    transform: rotate(30deg) !important;
                }

                .trep {
                    font-size: 20px;

                    @media (max-width: 1024px) {
                        font-size: 16px;
                    }

                    @media (max-width: 1024px) {
                        font-size: 14px;
                    }
                }

                button {
                    background: transparent;
                    width: 100%;
                    max-width: 941px;
                    border: 0;
                    text-align: left;
                    font-size: 24px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: normal;
                    font-family: var(--int);
                    color: #fff;

                    @media (max-width: 1600px) {
                        font-size: 20px;
                    }

                    @media (max-width: 1024px) {
                        font-size: 16px;
                    }
                }

                .inside {
                    width: 100%;
                    display: flex;
                    justify-content: space-between;
                }
            }
        }

        .title {
            margin-left: 13.021vw;
            position: relative;

            h1 {
                font-size: 83.435px;
                font-style: normal;
                font-weight: 500;
                line-height: normal;
                font-family: var(--fog);
                color: #fff;
                margin: 0;

                @media (max-width: 1024px) {
                    font-size: 24px;
                    margin-bottom: 10px;
                }
            }

            .covertitle {
                position: absolute;
                top: -25px;
                width: 0;
                transition: all .3s ease;
                overflow: hidden;

                @media (max-width: 1024px) {
                    top: -10px;
                }

                h2 {
                    font-size: 111.247px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: normal;
                    font-family: var(--hit);
                    color: #F00;
                    margin: 0;
                    transition: all .3s ease;
                    white-space: nowrap;

                    @media (max-width: 1024px) {
                        font-size: 32px;
                    }
                }
            }
        }
    }

    .about {
        margin: 110px 0 0;

        padding: 0 100px 0;

        @media (max-width: 1600px) {
            padding: 0 50px;
        }

        @media (max-width: 1024px) {
            margin: 40px 0 0;
            padding: 0 20px 0;
        }

        .about__block {
            margin-top: -20px;
            display: flex;
            gap: 20px;
            align-items: flex-start;

            @media (max-width: 1600px) {
                flex-direction: column;
                justify-content: center;
                align-items: center;
            }

            @media (max-width: 1024px) {
                margin-top: 10px;
            }



            .aboutBlocks {
                .abt3 {
                    margin: 15px;
                }

                div {
                    display: flex;

                    img {
                        @media (max-width: 1024px) {
                            max-width: 50%;
                        }
                    }

                    .link {
                        position: relative;
                        display: flex;
                        align-items: center;
                        gap: 7px;
                        cursor: pointer;
                        margin-right: 100px;
                        text-decoration: none;
                        white-space: nowrap;

                        @media (max-width: 500px) {
                            margin-right: 50px;
                        }

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

                            @media (max-width: 1024px) {
                                font-size: 12px;
                            }
                        }

                        .linkbg {
                            position: absolute;
                        }

                        img {
                            opacity: 0;
                            transition: .3s ease;
                            max-width: 100%;
                        }

                        &:hover img {
                            opacity: 1;
                        }
                    }
                }
            }

            p {
                font-size: 20px;
                font-style: normal;
                font-weight: 400;
                line-height: 150%;
                font-family: var(--int);
                color: #fff;
                max-width: 500px;

                @media (max-width: 1600px) {
                    max-width: 100%;
                }

                @media (max-width: 1024px) {
                    font-size: 16px;
                }
            }
        }

        .title {
            position: relative;

            h1 {
                font-size: 83.435px;
                font-style: normal;
                font-weight: 500;
                line-height: normal;
                font-family: var(--fog);
                color: #fff;
                margin: 0;

                @media (max-width: 1024px) {
                    font-size: 24px;
                    margin-bottom: 10px;
                }
            }

            .covertitle {
                position: absolute;
                top: -25px;
                width: 0;
                transition: all .3s ease;
                overflow: hidden;

                @media (max-width: 1024px) {
                    top: -10px;
                }

                h2 {
                    font-size: 111.247px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: normal;
                    font-family: var(--hit);
                    color: #F00;
                    margin: 0;
                    transition: all .3s ease;
                    white-space: nowrap;

                    @media (max-width: 1024px) {
                        font-size: 32px;
                    }
                }
            }
        }
    }

    .newest {
        margin: 140px 0 0;

        padding: 0 125px;

        @media (max-width: 1600px) {
            padding: 0 50px;
        }

        @media (max-width: 1024px) {
            padding: 0 20px;
            margin: 38px 0 0;
        }

        .catalog {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(310px, 1fr));
            gap: 30px;
            grid-auto-flow: dense;
            margin: -20px 0 0;

            @media (max-width: 1024px) {
                margin-top: 0;
                gap: 20px;
                grid-template-columns: repeat(2, 1fr);
            }

            .catalog__item {
                background: #000;
                padding: 10px;
                text-decoration: none;

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

                &:last-child {
                    @media (max-width: 1024px) {
                        grid-column: span 2;
                        /* Занимает все 2 колонки в сетке */
                    }
                }
            }


        }

        .title {
            position: relative;

            h1 {
                font-size: 83.435px;
                font-style: normal;
                font-weight: 500;
                line-height: normal;
                font-family: var(--fog);
                color: #fff;
                margin: 0;

                @media (max-width: 1024px) {
                    font-size: 24px;
                    margin-bottom: 10px;
                }
            }

            .covertitle {
                position: absolute;
                top: -25px;
                width: 0;
                transition: all .3s ease;
                overflow: hidden;

                @media (max-width: 1024px) {
                    top: -10px;
                }

                h2 {
                    font-size: 111.247px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: normal;
                    font-family: var(--hit);
                    color: #F00;
                    margin: 0;
                    transition: all .3s ease;
                    white-space: nowrap;

                    @media (max-width: 1024px) {
                        font-size: 32px;
                    }
                }
            }
        }
    }

    .urstyle {
        position: relative;

        .style {
            position: relative;
            z-index: 3;
        }

        .line2 {
            position: absolute;
            z-index: 1;
            top: 50%;
            left: -100px;
            background: #F00;
            transform: rotate(-20deg);
            width: 150%;
            overflow: hidden;


        }

        .line {
            z-index: 2;
            position: absolute;
            top: 73%;
            left: -100px;
            background: #fff;
            transform: rotate(20deg);
            width: 150%;
            overflow: hidden;

            @media (max-width: 1600px) {
                top: 60%;
            }
        }

        .running-text {
            min-height: 50px;
            width: 100%;
            position: relative;
            padding-top: 12px;
            white-space: nowrap;

            @media (max-width: 1024px) {
                min-height: 10px;
                padding-top: 2px;
            }
        }

        .text-container {
            display: flex;
            animation: marquee 45s linear infinite;
        }

        .text-segment {
            margin-right: 40px;
            font-size: 20px;
            font-style: normal;
            font-weight: 500;
            line-height: normal;
            text-transform: uppercase;
            font-family: var(--int);
            color: #000;

            @media (max-width: 1024px) {
                font-size: 15px;
            }
        }

        @keyframes marquee {
            0% {
                transform: translateX(0);
            }

            100% {
                transform: translateX(calc(-100% + 1rem));
            }
        }
    }

    .popular {
        margin-top: 100px;
        padding: 0 125px 0;

        @media (max-width: 1600px) {
            padding: 0 50px;
        }

        @media (max-width: 1024px) {
            padding: 0 20px;
            margin-top: 45px;
        }

        .catalog {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(310px, 1fr));
            gap: 30px;
            grid-auto-flow: dense;
            margin: -20px 0 0;

            @media (max-width: 1024px) {
                margin-top: 0;
                gap: 20px;
                grid-template-columns: repeat(2, 1fr);
            }

            .catalog__item {
                background: #000;
                padding: 10px;
                text-decoration: none;

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

                &:last-child {
                    @media (max-width: 1024px) {
                        grid-column: span 2;
                        /* Занимает все 2 колонки в сетке */
                    }
                }
            }


        }


        .title {
            position: relative;

            h1 {
                font-size: 83.435px;
                font-style: normal;
                font-weight: 500;
                line-height: normal;
                font-family: var(--fog);
                color: #fff;
                margin: 0;

                @media (max-width: 1024px) {
                    font-size: 24px;
                    margin-bottom: 10px;
                }
            }

            .covertitle {
                position: absolute;
                top: -25px;
                width: 0;
                transition: all .3s ease;
                overflow: hidden;

                @media (max-width: 1024px) {
                    top: -10px;
                }

                h2 {
                    font-size: 111.247px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: normal;
                    font-family: var(--hit);
                    color: #F00;
                    margin: 0;
                    transition: all .3s ease;
                    white-space: nowrap;

                    @media (max-width: 1024px) {
                        font-size: 32px;
                    }
                }
            }
        }
    }

    .main {
        padding: 130px 0 0;
        position: relative;

        .redline {
            position: absolute;
            bottom: -25px;

            @media (max-width: 1024px) {
                bottom: 0;
                position: relative;
                margin-top: -82px;
                width: 100%;
                display: none;
            }

            @media (max-width: 500px) {
                margin-top: -35px;
            }
        }

        .redlinemob {
            display: none;

            @media (max-width: 1024px) {
                display: block;
            }
        }




        .links {
            display: flex;
            justify-content: center;
            align-items: center;


            .centered {
                margin: 0 5.521vw 0 6.927vw;

                @media (max-width: 1600px) {
                    margin: 0;
                    max-width: 50%;
                }

                @media (max-width: 1024px) {
                    max-width: 100%;
                }
            }

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

                @media (max-width: 1024px) {
                    font-size: 12px;
                }
            }

            .link {
                position: relative;
                display: flex;
                align-items: center;
                gap: 7px;
                cursor: pointer;

                @media (max-width: 1024px) {
                    display: none;
                }

                .linkbg {
                    position: absolute;
                }

                img {
                    opacity: 0;
                    transition: .3s ease;
                }

                &:hover img {
                    opacity: 1;
                }
            }
        }

        .mob {
            display: none;

            @media (max-width: 1024px) {
                display: flex;
                justify-content: space-between;
                padding: 20px 39px 0 44px;
            }

            img {
                display: none;
            }

            .link {
                display: flex !important;
            }
        }
    }
}
</style>