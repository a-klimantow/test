<template>
    <ul class="services__list">
        <li v-for="service in services" :key="service.name">
            <a href="#" class="services__link"
               :class="{'services__link--active': service.active}"
               :style="service.style"
               @click="changeActive(services, service)"
               :title="service.desc">
                {{ service.name }}
            </a>
        </li>
    </ul>
</template>

<script>
export default {
    props: {
        changeActive: Function
    },
    data() {
        return {
            services: [
                {
                   name: 'ХВС',
                   active: true,
                   style: {
                       color: '#3B75D8'
                   },
                   desc: 'Холодная вода'
                },
                {
                   name: 'ГВС',
                   active: false,
                   style: {
                       color: '#CE6381'
                   },
                   desc: 'Горячая вода'
                },
                {
                   name: 'Тепло',
                   active: false,
                   style: {
                       color: '#FF8A00'
                   },
                   desc: 'Теплоснабжение'
                },
                {
                   name: 'ЭЭ',
                   active: false,
                   style: {
                       color: '#2DAA76'
                   },
                   desc: 'Электроэнергия'
                }
            ]
        }
    }
}
</script>

<style>
    .services__list {
        display: flex;
    }

    .services__link {
        display: inline-flex;
        justify-content: center;
        align-items: center;
        min-width: 53px;
        min-height: 20px;
        background-color: #fff;
        margin-right: 4px;
        opacity: .6;
    }
    
    .services__list li:first-child {
        border-radius: 8px 0 0 0 ;
        overflow: hidden;
    }

    .services__link--active {
        opacity: 1;
    }

    
</style>
