<template>
    <div class="page">
        <prevPage></prevPage>

        <div class="product">
            <div class="inputs">
                <div class="blot">
                    <img src="@/assets/img/blot.svg" class="blotimg" alt="">
                </div>
                <div>
                    <label for="name">Название товара:</label>
                    <input type="text" placeholder="Введите название">
                </div>

                <div>
                    <label for="category">Категория товара:</label>

                    <div class="category">
                        <select v-model="selectedCategoryId" @change="updateSelectedCategory">
                            <option value="" selected disabled>Выберите</option>
                            <option value="1">Верх</option>
                            <option value="2">Низ</option>
                            <option value="3">Аксессуары</option>
                            <option value="4">Головные уборы</option>
                            <option value="5">Обувь</option>
                            <option value="6">Костюм</option>
                        </select>
                        <div v-if="selectedCategoryId !== null" class="selected">
                            <span>{{ getCategoryNameById(selectedCategoryId) }}</span>
                            <img src="@/assets/img/deletecat.svg" alt="" @click="clearSelectedCategory" />
                        </div>
                    </div>
                </div>

                <div class="price">
                    <label for="price">Цена:</label>
                    <input type="number" placeholder="Введите цену">
                </div>

                <div>
                    <label for="material">Материал изделия:</label>
                    <textarea name="material" id="material" cols="30" rows="6" placeholder="Введите данные"></textarea>
                </div>

                <div>
                    <label for="size">Размеры:</label>
                    <div>

                        <select v-model="selectedSize" @change="updateSelectedSize" v-if="selectedCategoryId != 5">
                            <option value="" disabled selected>Выберите размеры</option>
                            <option value="S">S</option>
                            <option value="M">M</option>
                            <option value="L">L</option>
                            <option value="XL">XL</option>
                        </select>


                        <input type="text" v-model="customSize" @keyup.enter="addCustomSize" placeholder="Введите размер"
                            v-else>

                    </div>

                    <div class="sizes">
                        <div v-for="(size, index) in sizes" :key="index">
                            <span>{{ size }}</span>
                            <img src="@/assets/img/deletecat.svg" alt="" @click="removeSize(index)" />
                        </div>
                    </div>
                </div>

            </div>

            <div class="images">
                <div class="imgusik">
                    <div class="img">
                        <label for="img">Загрузка изображений (до 5)</label>

                        <div class="selecter" @click="openFileInput" @dragover.prevent @drop="handleDrop">
                            <span>Перетащите файлы сюда или откройте вручную</span>
                            <small>Открыть</small>
                        </div>

                        <div class="selected__images">
                            <div v-for="(image, index) in images" :key="index" class="item">
                                <div class="img">
                                    <img :src="image.url" :alt="`Image ${index + 1}`">
                                </div>
                                <div class="text-right">
                                    <small @click="removeImage(index)">Удалить</small>
                                </div>
                            </div>
                        </div>
                    </div>
                    <input ref="fileInput" type="file" style="display: none" @change="handleFileChange" multiple>
                    <div class="text-right">
                        <img src="@/assets/img/stranno.svg" class="roll" alt="">
                    </div>
                </div>

                <div class="description">
                    <label for="desc">Описание:</label>
                    <ClientOnly>
                        <QuillEditor theme="bubble" toolbar="full" v-model:content="description" contentType="html" />
                    </ClientOnly>
                </div>

                <div class="publish">
                    <button>Опубликовать</button>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            selectedCategoryId: null,
            selectedSize: '',
            customSize: '',
            sizes: [],
            images: [],
            maxImages: 5,
            description: '',
        };
    },
    watch: {
        customSize(value) {
            if (value && value.trim() && event.key === 'Enter') {
                this.addCustomSize();
            }
        },
    },
    methods: {
        openFileInput() {
            this.$refs.fileInput.click();
        },
        handleFileChange(event) {
            const files = event.target.files;
            this.addImages(files);
        },
        handleDrop(event) {
            event.preventDefault();
            const files = event.dataTransfer.files;
            this.addImages(files);
        },
        addImages(files) {
            for (let i = 0; i < files.length; i++) {
                if (this.images.length < this.maxImages) {
                    const reader = new FileReader();
                    reader.onload = (e) => {
                        this.images.push({ url: e.target.result, file: files[i] });
                    };
                    reader.readAsDataURL(files[i]);
                }
            }
        },
        removeImage(index) {
            this.images.splice(index, 1);
        },
        updateSelectedSize() {
            if (this.selectedSize && !this.sizes.includes(this.selectedSize)) {
                this.sizes.push(this.selectedSize);
            }
        },
        addCustomSize() {
            const size = this.customSize.trim();
            if (size && !this.sizes.includes(size)) {
                this.sizes.push(size);
                this.customSize = '';
            }
        },
        removeSize(index) {
            this.sizes.splice(index, 1);
        },
        clearSelectedCategory() {
            this.selectedCategoryId = null;
        },
        getCategoryNameById(id) {
            switch (id) {
                case '1':
                    return 'Верх';
                case '2':
                    return 'Низ';
                case '3':
                    return 'Аксессуары';
                case '4':
                    return 'Головные уборы';
                case '5':
                    return 'Обувь';
                case '6':
                    return 'Костюм';
                default:
                    return '';
            }
        },
    },
};
</script>
<script setup>
import { QuillEditor } from '@vueup/vue-quill';
import '@vueup/vue-quill/dist/vue-quill.snow.css';
import '@vueup/vue-quill/dist/vue-quill.bubble.css';

useSeoMeta({
    title: 'Редактирование товара | Most',
    ogTitle: 'Редактирование товара | Most',
    description: 'Редактирование товара | Most',
    ogDescription: 'Редактирование товара | Most',
})

</script>
<style lang="scss" scoped>
.page {
    padding: 125px 100px 100px;

    @media (max-width: 1600px) {
        padding: 125px 50px 50px;
    }

    @media (max-width: 1024px) {
        padding: 125px 20px 50px;
    }

    .product {
        display: flex;
        justify-content: space-between;
        margin-top: 30px;

        @media (max-width: 1024px) {
            flex-direction: column;
            gap: 30px;
        }

        .images {
            width: 100%;
            max-width: 52.135vw;

            @media (max-width: 1024px) {
                max-width: 100%;
            }

            .description {
                margin-top: 15px;

                label {
                    font-size: 20px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: 130%;
                    font-family: var(--int);
                    color: #fff;
                }
            }

            .publish {
                text-align: left;
                margin-top: 30px;

                @media (max-width: 1024px) {
                    margin: 20px 0 0;
                    text-align: right;
                }

                button {
                    padding: 10px 30px;
                    border: 1px solid #f00;
                    background: transparent;

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
            }

            .img {
                .selected__images {
                    margin-top: 20px;
                    display: grid;
                    grid-template-columns: repeat(auto-fill, minmax(170px, 1fr));
                    gap: 20px;
                    grid-auto-flow: dense;

                    .item {
                        .img {
                            padding: 10px;
                            background: #000;
                            border: 1px solid #f00;

                            img {
                                width: 100%;
                                height: 150px;
                                object-fit: cover;
                            }
                        }

                        small {
                            font-size: 12px;
                            font-style: normal;
                            font-weight: 400;
                            line-height: normal;
                            text-decoration-line: underline;
                            font-family: var(--int);
                            color: #7C5555;
                            cursor: pointer;
                        }
                    }
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

                .selecter {
                    border: 1px solid #f00;
                    padding: 11px 15px 13px;
                    display: flex;
                    align-items: center;
                    justify-content: space-between;
                    cursor: pointer;

                    span,
                    small {
                        font-size: 20px;
                        font-style: normal;
                        font-weight: 400;
                        line-height: 130%;
                        font-family: var(--int);
                        color: #fff;
                        opacity: 0.7;

                        @media (max-width: 1024px) {
                            font-size: 16px;
                        }
                    }

                    small {
                        text-decoration: underline;
                    }
                }
            }
        }

        .inputs {
            width: 100%;
            max-width: 28.125vw;
            display: flex;
            flex-direction: column;
            gap: 30px;
            position: relative;

            @media (max-width: 1024px) {
                max-width: 100%;
            }


            option {
                color: #fff;
                background: #000;
                font-family: var(--int);
                font-size: 16px;
            }

            .price {
                input {
                    max-width: 290px;
                }
            }

            .sizes {
                margin-top: 30px;
                display: flex;
                align-items: flex-start;
                gap: 30px;

                div {
                    display: flex;
                    justify-content: center;
                    flex-wrap: wrap;
                    align-items: center;
                    padding: 15px;
                    gap: 12px;

                    border: 1px solid #f00;

                    span {
                        font-size: 16px;
                        font-style: normal;
                        font-weight: 400;
                        line-height: 130%;
                        font-family: var(--int);
                        color: #fff;
                    }

                    img {
                        cursor: pointer;
                    }
                }
            }

            .category {
                display: flex;
                flex-wrap: wrap;
                gap: 30px;

                select {
                    flex: 1;
                }



                .selected {
                    flex: 1;
                    width: 100%;
                    display: flex;
                    align-items: center;
                    justify-content: space-between;
                    max-width: 220px;
                    padding: 12px 10px;
                    border: 1px solid #f00;

                    font-size: 20px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: 130%;
                    font-family: var(--int);
                    color: #fff;

                    @media (max-width: 1024px) {
                        font-size: 16px;
                    }

                    img {
                        cursor: pointer;
                    }
                }
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

            input,
            select,
            textarea {
                width: 100%;
                padding: 12px 10px;
                background: transparent;
                border: 1px solid #f00;

                font-size: 20px;
                font-style: normal;
                font-weight: 400;
                line-height: 130%;
                font-family: var(--int);
                color: #fff;

                @media (max-width: 1024px) {
                    font-size: 16px;
                }

                &::placeholder {
                    opacity: 0.7;
                }
            }
        }

        .blotimg {
            transition: transform .3s ease;
            animation: scale 1.5s linear infinite;
            position: absolute;
            left: 30%;
        }

        .roll {
            transition: transform .3s ease;
            animation: rotate 2s linear infinite;
        }

        @keyframes rotate {
            from {
                transform: rotate(0deg);
            }

            to {
                transform: rotate(360deg);
            }
        }

        @keyframes scale {
            from {
                transform: scale(0);
            }

            to {
                transform: scale(1);
            }
        }
    }
}
</style>