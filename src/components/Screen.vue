<template>
    <div class="screen"> 
        <!-- Разметка гафика -->
        <ul class="screen__block">
            <li class="screen__row"
                v-for="row in rows" :key="row">
                <span class="screen__number">{{ row | currentNumber }}</span>
            </li>
        </ul>
    </div>
</template>

<script>
import Vue from 'vue';

Vue.filter('currentNumber', function(value) {
    return String(value).slice(0,-3) + ' ' + String(value).slice(-3)
})

export default {
    data() {
        return {
            rows: [100000, 200000, 300000, 400000, 500000]
        }
    }
}
</script>

<style>
    .screen, .screen__block{
        height: 100%;
        width: 100%;
        top: 0;
        left: 0;
        position: absolute;
    }

    .screen__block {
        border-bottom: 1px solid var(--color-grey-lite);
        display: flex;
        flex-direction: column-reverse;
        justify-content: space-between;
        overflow: hidden;
    }

    .screen__row {
        flex-basis: 100%;
        border-top: 1px solid var(--color-grey-lite);
        padding-left: 27px;
        position: relative;
    }
    
    .screen__number {
        font-size: 10px;
        color: var(--color-grey);
        position: absolute;
        top: -13px;
    }

</style>
