<template>
    <ul class="devices__list">
        <li class="devices__item"
            v-for="device in devices" :key="device.name">
            <a href="#" class=devices__link
               :class="{'devices__link--active': device.active}"
               @click="changeActive(devices, device)">
                {{ device.name }}
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
            devices: [
                {
                    name: 'ИПУ',
                    active: false
                },
                {
                    name: 'ОДПУ',
                    active: false
                },
                {
                    name: 'СОИ',
                    active: true
                }
            ]
        }
    }
}
</script>

<style>
    .devices__list {
        display: flex;
        border: 1px solid var(--color-blue);
        border-radius: 16px;
        overflow: hidden;
    }

    .devices__item {
        border-left: 1px solid var(--color-blue);
    }

    .devices__item:first-child {
        border-left: none;
    }

    .devices__link {
        display: inline-block;
        width: 56px;
        height: 18px;
        display: inline-flex;
        justify-content: center;
        align-items: center;
        color: var(--color-black);
    }

    .devices__link--active {
        background-color: var(--color-blue);
        color: #fff;
    }

</style>
