<template>
    <section class="info-block">

        <!-- Заголовок -->
        <header class="info-block__header">
            <h2>Корабельная, д. {{ userData.number }}</h2>
            <div class="info-block__header--service">ХВС</div>
        </header>
        <div class="info-block__content">
        
            <!-- План -->
            <div class="info-block__item">
                <h3>План</h3>
                {{ userData.plan | currentNumber }} м<sup>2</sup>
            </div>
        
            <!-- Факт -->
            <div class="info-block__item">
                <h3>Факт</h3>
                {{ userData.fact | currentNumber }} м<sup>2</sup>
            </div>
        
            <!-- СОИ -->
            <div class="info-block__item soi">
                <h3>СОИ</h3>
                <div v-if="soi > 0">
                    {{ soi | currentNumber }} м<sup>2</sup>
                </div>
            </div>
        
            <!-- Ошибка если есть -->
            <div class="info-block__item error"
                v-show="soi > 0">
                Причина: несвоевременная реакция на  <span>аварию в системе ГВС</span>
            </div>
        
            <!-- Колличество квартир -->
            <div class="info-block__item">
                <h3>Квартир/л.счетов</h3>
                {{ userData.apartaments }}
            </div>
        
            <!-- Общая площадь -->
            <div class="info-block__item">
                <h3>Общая площадь</h3>
                {{ userData.totalArea | currentNumber }} м<sup>2</sup>
            </div>
        
            <!-- Жилая Площадь -->
            <div class="info-block__item">
                <h3>Жилая Площадь</h3>
                {{ userData.livingSpace | currentNumber }} м<sup>2</sup>
            </div>
        
            <!-- Узлы учета -->
            <div class="info-block__item">
                <h3>Узлов учета</h3>
                {{ userData.meteringStation }}
            </div>
        
            <!-- Узлы реагирования -->
            <div class="info-block__item">
                <h3>Узлов реагирования</h3>
                {{ userData.responseStation }}
            </div>
        </div>
    </section>
</template>

<script>
import Vue from 'vue';

Vue.filter('currentNumber', function(value) {
    if(value > 999999) {
        return String(value).slice(0, -6) + ' ' + String(value).slice(-6, -3) + ' ' + String(value).slice(-3)
    }
    return String(value).slice(0,-3) + ' ' + String(value).slice(-3)
})

export default {
    props: {
        userData: Object,
        soi: Number
    }
}
</script>

<style>
    .info-block {
        background-color: #fff;
        min-height: 300px;
        border-radius: 8px;
        padding: 20px;
        height: 100%;
    }

    .info-block__header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        font-size: 18px;
        margin-bottom: 15px;
    }

    .info-block__header h2 {
        font-weight: normal;
    }

    .info-block__header--service {
        color: var(--color-blue);
    }

    .info-block__content {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
    }

    .info-block__item {
        padding: 8px;
        font-size: 16px;
        display: flex;
        flex-wrap: wrap;
        align-self: stretch;
        margin-bottom: 15px;
    }

    .info-block__item.soi {
        color: var(--color-red);
    }

    .info-block__item h3 {
        color: #A5AEBE;
        font-weight: normal;
        font-size: 12px;
        width: 100%;
    }

    .error {
        grid-column: 1 / -1;
        border: 1px solid rgba(188, 83, 121, 0.6);
        text-align: center;
        font-size: 12px;
        border-radius: 4px;
    }

    .error>span {
        color: var(--color-blue);
    }

    
</style>
