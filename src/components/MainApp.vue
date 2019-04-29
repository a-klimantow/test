<template>
    <main class="main-container">

        <!-- Главный блок -->
        <div class="main-container__content">
            <services :changeActive="changeActive"></services>
            <div class="main-container__block-top">
                <div class="main-container__row">
                    <devices :changeActive="changeActive"></devices>
                    <calendar></calendar>
                </div>
                <div class="main-container__row">
                    <span>{{ data.street }}</span>
                    <span>ул. Ленина</span>
                </div>
                <div class="main-container__screen">
                    <screen></screen>
                    <UserStatus :house-list="data.houseList"
                                @indexUserClick="handleInfo"></UserStatus> 
                </div>
            </div>
        </div>

        <!-- Полная информация выводится по клику на дом -->
        <div class="main-content__info">
            <user-info :user-data="data.houseList[index]"
                       :soi="soi"
                       v-if="hiddenPanel">
            </user-info>
        </div>
        
        <!-- План на следующий месяц для дома выводится по клику-->
        <div class="main-content__plan">
            <user-plan v-if="hiddenPanel"></user-plan>
        </div>
    </main> 
</template>

<script>
import Services from './Services.vue'
import Devices from './Devices.vue'
import Calendar from './Calendar.vue'
import Screen from './Screen.vue'
import UserStatus from './UserStatus.vue'
import UserInfo from './UserInfo.vue'
import { info } from './data.js'
import UserPlan from './UserPlan.vue'

export default {
    props: {
        changeActive: Function,
        info: Object
    },
    components: {
        Services,
        Devices,
        Calendar,
        Screen,
        UserStatus,
        UserInfo,
        UserPlan
    },
    data() {
        return {
            data : info,
            index: null,
            soi: 0,
            hiddenPanel: false
        }
    },
    methods: {
        handleInfo(index, soi) {
            this.hiddenPanel = true
            this.index = index;
            this.soi = soi
        }
    }
}
</script>

<style>
    .main-container {
        background-color: #F3F6FC;
        padding: 35px;
        grid-area: main;
        display: inherit;
        grid-template-areas: 
            'content content'
            'allInfo plan';
        grid-gap: 20px;
        grid-template-columns: 2fr 1fr;
        align-content: start;
    }

    .main-container__content {
        grid-area: content;
    }

    .main-container__block-top {
        background-color: #fff;
        min-height: 355px;
        border-radius: 0 8px 8px 8px;
        padding-bottom: 44px;
        display: flex;
        flex-direction: column;
        
    }

    .main-container__row  {
        min-height: 45px;
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 0 30px;
    }

    .main-container__screen {
        flex-grow: 1;
        position: relative;
    }

    .main-content__plan {

    }
</style>
