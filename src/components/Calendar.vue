<template>
    <div class="calendar">
        <a href="#">
            <i class="fas fa-chevron-left calendar__icon"></i>
        </a>
        <time class="calendar__date">Март 2019</time>
        <a href="#" class="disabled">
            <i class="fas fa-chevron-right calendar__icon"></i>
        </a>


    </div>
</template>

<script>
export default {
    
}
</script>

<style>
    .calendar {
        color: var(--color-blue);
    }

    .calendar__date {
        margin: 0 8px;
    }

    .disabled {
        color: #D1D6DF;
    }

</style>
