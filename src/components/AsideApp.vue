<template>
    <aside class="main-aside">
        <ul>
            <li class="main-aside__item"
                v-for="item in menuItems" :key="item.name">
                <a href="#" class="main-aside__link" 
                            :class="{'main-aside__link--active': item.active}"
                            @click="changeActive(menuItems, item)">
                    <i class="fas main-aside__icon" :class="[item.icon]"></i>
                    {{ item.name }}
                </a>
                <p class="main-aside__text"
                   v-if="item.name === 'Поиск'">
                        По личным данным, ФИО или адресу
                   </p>
            </li>
        </ul>
    </aside>    
</template>

<script>
export default {
    props: {
        changeActive: Function
    },
    data() {
        return {
            menuItems: [
                {
                    name: 'Рабочий стол',
                    icon: 'fa-desktop',
                    active: true
                },
                {
                    name: 'Дома',
                    icon: 'fa-building',
                    active: false
                },
                {
                    name: 'Абоненты',
                    icon: 'fa-users',
                    active: false
                },
                {
                    name: 'Запросы на изменение',
                    icon: 'fa-comment-dots',
                    active: false
                },
                {
                    name: 'Поиск',
                    icon: 'fa-search',
                    active: false
                }
            ]
        }
    }
}
</script>

<style>
    .main-aside {
        background-color: #fff;
        padding: 15px 30px;

        grid-area: menu;
    }

    .main-aside__link {
        display: flex;
        align-items: center;
        min-height: 80px;
        font-size: 14px;
        color: var(--color-black);
        transition: color .5s ease-in-out;
    }

    .main-aside__link:hover {
        color: var(--color-blue);
    }

    .main-aside__link:hover .main-aside__icon {
        opacity: 1;
    }

    .main-aside__icon {
        display: inherit;
        justify-content: center;
        align-items: center;
        font-size: 1.4em;
        width: 35px;
        height: 35px;
        border-radius: 50%;
        background-color: #fff;
        margin-right: 10px;
        color: var(--color-blue);
        opacity: 0.8;
        transition: background-color .5s, color .5s;
    }

    .main-aside__link--active {
        color: var(--color-blue);
        font-weight: bold;
        position: relative;
    }

    .main-aside__link--active::after {
        content: '';
        position: absolute;
        width: 3px;
        height: 32px;
        background-color: var(--color-blue);
        right: -30px;
    }

    .main-aside__link--active .main-aside__icon {
        color: #fff;
        background-color: var(--color-blue);
        opacity: 1;
    }

    .main-aside__text {
        margin: 0;
        padding-left: 42px;
        padding-right: 10px;
        transform: translateY(-25px);
        opacity: .5;
        position: relative;
    }

</style>
