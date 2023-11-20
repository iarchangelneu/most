<template>
    <div class="empty" v-if="transactions.length <= 0">
        <div class="text-center">
            <h1>список операций будет доступен после пополнения средств</h1>

            <div class="text-right">
                <img src="@/assets/img/empty.png" class="img-fluid" alt="">
            </div>
        </div>
    </div>
    <div class="transactions" v-else>
        <div class="pc">
            <table class="table table-borderless text-center">
                <thead>
                    <tr>
                        <th scope="col">Тип</th>
                        <th scope="col">Цена</th>
                        <th scope="col">Дата/Время</th>
                        <th scope="col">Статус</th>
                        <th scope="col">Состояние счета</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="item in transactions" :key="item.id">
                        <td>{{ item.type_operation }}</td>
                        <td>{{ item.amount.toLocaleString() }} ₸</td>
                        <td>{{ formatDate(item.date) }}</td>
                        <td class="success" :class="{ success: item.paid == 1, failure: item.paid == 0 }">{{ item.paid == 1
                            ? 'Совершено' :
                            item.paid == 0 ? 'Отменено' : item.paid }}</td>
                        <td>{{ Math.floor(item.amount_now).toLocaleString() }} ₸</td>
                    </tr>
                </tbody>
            </table>
        </div>

        <div class="mob">
            <div class="mob__item">
                <div class="item__header">
                    <span>Пополнение</span>
                    <small>29.11.22 18:08</small>
                    <img src="@/assets/img/success.svg" alt="">
                </div>

                <div class="item__body">
                    <div>
                        <span>Цена</span>
                        <small>+ 18 000 ₸</small>
                    </div>
                    <div>
                        <span>Состояние счета</span>
                        <small>10 000 ₸</small>
                    </div>
                </div>
            </div>
            <div class="mob__item" v-for="item in transactions" :key="item.id">
                <div class="item__header">
                    <span>{{ item.type_operation }}</span>
                    <small>{{ formatDate(item.date) }}</small>
                    <img src="@/assets/img/success.svg" v-if="item.paid == 1" alt="">
                    <img src="@/assets/img/failure.svg" v-else alt="">
                </div>

                <div class="item__body">
                    <div>
                        <span>Цена</span>
                        <small>{{ item.amount.toLocaleString() }} ₸</small>
                    </div>
                    <div>
                        <span>Состояние счета</span>
                        <small>{{ Math.floor(item.amount_now).toLocaleString() }} ₸</small>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    props: {
        transactions: [],
    },
    data() {
        return {
            test: false,
        }
    },
    methods: {
        calculateAmountNow(item) {
            if (item.type_operation === 'ВЫВОД' && item.paid === 0) {
                return (item.amount_now + item.amount).toLocaleString();
            } else if (item.type_operation === 'ПОПОЛНЕНИЕ' && item.paid === 0) {
                return (item.amount_now - item.amount).toLocaleString();
            } else {
                return item.amount_now.toLocaleString();
            }
        },
        formatDate(dateTime) {
            const date = new Date(dateTime);

            const day = String(date.getDate()).padStart(2, '0');
            const month = String(date.getMonth() + 1).padStart(2, '0');
            const year = String(date.getFullYear()).slice(-2);
            const hours = String(date.getHours()).padStart(2, '0');
            const minutes = String(date.getMinutes()).padStart(2, '0');

            return `${day}.${month}.${year} ${hours}:${minutes}`;
        },
    }
}
</script>
<script setup>
useSeoMeta({
    title: 'Транзакции | Most',
    ogTitle: 'Транзакции | Most',
    description: 'Транзакции | Most',
    ogDescription: 'Транзакции | Most',
})
</script>
<style lang="scss" scoped>
.empty {
    width: 100%;

    h1 {
        font-size: 40px;
        font-style: normal;
        font-weight: 400;
        line-height: normal;
        font-family: var(--tka);
        color: #fff;
        margin: 0 0 70px;

        @media (max-width: 1024px) {
            font-size: 20px;
        }
    }

    .text-right {
        @media (max-width: 1024px) {
            text-align: center !important;
        }
    }

}

.transactions {
    width: 100%;

    .mob {
        display: none;

        @media (max-width: 1024px) {
            display: flex;
            flex-direction: column;
        }

        .mob__item {
            padding: 30px;
            border-bottom: 1px solid #fff;

            &:last-child {
                border: 0;
            }

            .item__header,
            .item__body {
                display: flex;
                justify-content: space-between;
            }

            .item__body {
                margin-top: 15px;

                div {
                    display: flex;
                    flex-direction: column;
                    gap: 10px;
                }
            }

            span,
            small {
                font-size: 16px;
                font-style: normal;
                font-weight: 500;
                line-height: normal;
                font-family: var(--int);
                color: #fff;
            }

            small {
                font-weight: 400;
            }
        }
    }

    .pc {
        @media (max-width: 1024px) {
            display: none;
        }

        table {
            th {
                font-size: 36px;
                font-style: normal;
                font-weight: 700;
                line-height: normal;
                font-family: var(--tka);
                color: #fff;

                @media (max-width: 1400px) {
                    font-size: 25px;
                }
            }

            .success {
                color: #03B820 !important;
            }

            .failure {
                color: #EA0505 !important;
            }

            td {
                font-size: 24px;
                font-style: normal;
                font-weight: 400;
                line-height: normal;
                font-family: var(--int);
                color: #fff;

                @media (max-width: 1400px) {
                    font-size: 18px;
                }
            }
        }
    }
}
</style>