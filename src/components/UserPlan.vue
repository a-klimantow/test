<template>
    <div class="user-plan">
        <h2>В следующем месяце</h2>
        <p>
            <span>План</span>
            250 000 м<sup>2</sup>
        </p>
        <p>
            <span>Предпол. факт</span>
            245 000 м<sup>2</sup>
        </p>
        <p>
            <span>Факторы прогноза</span>
            Авария в 4 подъезде,
            сезонные работы
        </p>
        <button>подробнее</button>
    </div>    
</template>

<script>
export default {
    
}
</script>

<style>
    .user-plan {
        height: 100%;
        background-color: #fff;
        box-shadow: 0px 4px 8px rgba(102, 120, 149, 0.04);
        border-radius: 8px;
        padding: 25px;
    }

    .user-plan h2 {
        margin-bottom: 24px;
    }

    .user-plan p {
        font-size: 16px;
        min-height: 30px;
        margin-bottom: 20px;
    }

    .user-plan span {
        color: #A5AEBE;
        display: block;
        font-size: 12px;
        margin-bottom: .5em;
    }

    .user-plan button {
        background: linear-gradient(360deg, #5C96F8 50%, #124EB4 175%);
        box-shadow: 0px 4px 4px rgba(156, 192, 249, 0.4);
        border-radius: 32px;
        color: #fff;
        text-transform: uppercase;
        border: none;
        display: inline-block;
        padding: .5em 2em;
    }
</style>
