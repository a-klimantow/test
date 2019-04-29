<template>
    <header class="main-header">
        <div class="main-header__logo">
            <b>Система ЖКХ</b>
        </div>
        <div class="main-header__company">
            <i class="fas fa-user main-header__company--icon"></i>
            УК "Северная звезда"
        </div>
        <a href="#" class="main-header__logout">
            Выход
            <span class="main-header__logout--icon"></span>
        </a>
    </header>
</template>

<script>
export default {
    
}
</script>

<style>
    .main-header {
        display: flex;
        align-items: center;
        min-height: 48px;
        padding: 0 30px;
        box-shadow: 0px 4px 8px rgba(153, 177, 195, 0.08);
        background-color: #fff;
        z-index: 10;

        grid-area: header;
    }
    .main-header__logo {
        color: var(--color-blue);
        flex-grow: 1;
    }

    .main-header__company {
        color: var(--color-black);
        display: inherit;
        justify-content: center;
        align-items: center;
        margin-right: 16px;
    }

    .main-header__company--icon {
        background-color: #BBC1C7;
        color: #fff;
        width: 23px;
        height: 23px;
        border-radius: 50%;
        margin-right: 8px;
        display: inherit;
        justify-content: center;
        align-items: center;
        font-size: 1.15em;
    }

    .main-header__logout {
        padding-left: 16px;
        border-left: 1px solid #C5C7CA;
        line-height: 20px;
        color: #C5C7CA;
        display: inherit;
        align-items: center;
    }

    .main-header__logout--icon {
        display: inline-block;
        width: 20px;
        height: 20px;
        margin-left: 8px;
        border: 2px solid var(--color-blue);
        border-radius: 50%;
        position: relative;
    }

    .main-header__logout--icon::after {
        content: '';
        border: inherit;
        border-radius: inherit;
        width: 45%;
        height: 45%;
        display: block;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
    }

    .main-header__logout--icon::before {
        content: '';
        display: block;
        height: 50%;
        width: 2px;
        background-color: var(--color-blue);
        border: 2px solid #fff;
        position: absolute;
        left: 50%;
        transform: translate(-50%, -50%);
    }

</style>
