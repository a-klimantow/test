<template>
    <div id="app">
        <HeaderApp></HeaderApp>
        <AsideApp :changeActive="changeActiveItem"></AsideApp>
        <MainApp :changeActive="changeActiveItem" style="min-height: 800px;"></MainApp>
    </div>
</template>

<script>
import HeaderApp from './components/HeaderApp.vue'
import AsideApp from './components/AsideApp.vue'
import MainApp from './components/MainApp.vue'

export default {
    name: 'app',
    components: {
        HeaderApp,
        AsideApp,
        MainApp
    },
    methods: {
        // Меняет класс c обычного на active
        changeActiveItem(arr, item) {
            arr.map((elem) => elem.active = false);
            item.active = true;
        }
    }
}
</script>

<style>
    :root {
        --color-blue: #5283D3;
        --color-black: #3A4352;
        --color-grey: #D1D6DF;
        --color-grey-lite: #F3F6FC;
        --color-red: #BC5379;
    }

    html, body {
        margin: 0;
        padding: 0;
        height: 100%;
    }

    body {
        font-family: 'Roboto', sans-serif;
        font-size: 12px;
        color: var(--color-black);
    }

    * {
        box-sizing: border-box;
    }

    a {
        text-decoration: none;
        outline: none;
        color: inherit;
    }

    ul, li {
        padding: 0;
        margin: 0;
        list-style: none;
    }

    h1, h2, h3, h4, h5, h6, p {
        margin: 0;
        padding: 0;
    }

    #app {
        max-width: 1152px;
        margin: 0 auto;
        display: grid;
        grid-template-areas:
            'header header'
            'menu main';
        grid-template-columns: 1fr 3fr;
    }
</style>
