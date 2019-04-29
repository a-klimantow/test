<template>
    <ul class="user__list">
        <li class="user__item"
            v-for="(house, index) in houseList" :key="house.number">
            <div class="status"
                 @click="showFullUserInfo(index)">
                <div class="status__error"
                     :style="showError(index)"></div>
                <div class="status__plan"
                     :style="showPlan(index)"></div>
                <div class="status__fact"
                     :style="showFact(index)"></div>
            </div>
            <span class="user__number">д. {{ house.number }}</span>
            <div class="user__info"
                 @click="showFullUserInfo(index)">
                <div class="user__info--item">
                    <h6>План</h6>
                    <p>
                        {{ houseList[index].plan | currentNumber }} м<sup>3</sup>
                    </p>
                </div>
                <div class="user__info--item">
                    <h6>Факт</h6>
                    <p>
                        {{ houseList[index].fact | currentNumber }} м<sup>3</sup>
                    </p>
                </div>
                <div class="user__info--item"
                    v-if="showSoi(index) > 0">
                    <h6>СОИ</h6>
                    <p>
                        {{ showSoi(index) | currentNumber }} м<sup>3</sup>
                    </p>
                </div>
             
            </div>
        </li>
    </ul>    
</template>

<script>
import Vue from 'vue';

Vue.filter('currentNumber', function(value) {
    return String(value).slice(0,-3) + ' ' + String(value).slice(-3)
})

export default {
    props: {
        houseList: Array
    },
    methods: {
        showPlan(index) {
            let res = 100 * this.houseList[index].plan / 500000
            return {
                height: res + '%'
            }
        },
        showFact(index) {
            if(this.houseList[index].fact > this.houseList[index].plan) {
            let res = 100 * this.houseList[index].plan / 500000
                return {
                    height: res + '%',
                    backgroundColor: 'transparent'
                }
            }
            let res = 100 * this.houseList[index].fact / 500000
                return {
                    height: res + '%'
                }
        },
        showError(index) {
            let res = 100 * this.houseList[index].fact / 500000
            return {
                height: res + "%"
            }
        },
        showSoi(index) {
            return this.houseList[index].fact - this.houseList[index].plan
            
        },
        showFullUserInfo(index) {
            let soi = this.showSoi(index);
            this.$emit('indexUserClick', index, soi);
        }
        
    }
}
</script>

<style>
    .user__list {
        width: 100%;
        height: 100%;
        position: relative;
        z-index: 1;
        padding-left: 100px;
        padding-right: 50px;
        display: flex;
        align-items: flex-end;
        justify-content: space-around;
    }
    
    .user__item {
        height: 100%;
        display: flex;
        flex-direction: column;
        position: relative;
    }

    .user__number {
        color: var(--color-black);
        position: absolute;
        width: 50px;
        bottom: 0;
        left: 50%;
        transform: translate(-50%, 150%);
        text-align: center;
    }

    .status {
        width: 12px;
        height: 100%;
        margin: 0 auto;
        border-radius: 2px;
        overflow: hidden;
        position: relative;
    }

    .status__error, .status__plan, .status__fact {
        width: 100%;
        position: absolute;
        bottom: 0;
        border-radius: 2px;
    }

    .status__error {
        background-color: #BC5379;
        height: 60%;
    }

    .status__fact {
        background-color: var(--color-blue);
        height: 50%;
        border-radius: 0;
        border-top: 2px solid #fff;
    }

    .status__plan {
        background-color: var(--color-grey);
        height: 50%;
    }

    .user__info {
        position: absolute;
        display: none;
        flex-wrap: wrap;
        background-color: #fff;
        min-width: 174px;
        box-shadow: 0px 1px 4px rgba(209, 216, 227, 0.67);
        border-radius: 4px;
        top: 40%;
        left: 50%;
        transform: translateX(-50%);
        z-index: 10;

    }

    .user__info::before {
        position: absolute;
        content: '';
        width: 9px;
        height: 9px;
        display: block;
        background-color: #fff ;
        bottom: 0;
        left: 50%;
        transform: translate(-50%, 50%) rotate(45deg);
    }

    .user__item:hover .user__info {
        display: flex;
    }

    .user__info--item {
        width: 50%;
        padding: 8px;
    }

    .user__info--item h6 {
        color: #A5AEBE;
    }
</style>
