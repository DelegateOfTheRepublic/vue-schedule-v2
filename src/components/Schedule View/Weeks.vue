<template>
<div class="week">
    <div class="week__info" v-if="size == 'standart'">
        <p>Текущая неделя: {{current_type_week}}</p>
        <p>По счету: {{week_number}}-я</p>
    </div>
    <div :class="['week__days', {'week__days--medium': size == 'medium'}]" v-if="size !== 'small'">
        <day-week v-for="i in 6" :key="i" :day_number="i"/>
    </div>
    <div :class="['week__days', {'week__days--small': size == 'small'}]" v-if="size == 'small'">
        <day-week v-for="i in 6" :key="i" :day_number="i" noDate="true"/>
    </div>
</div>
</template>

<script>
import DayWeek from '../DayWeek.vue'

export default {
    components: { DayWeek },
    props: {
        size: {
            type: String,
            default: 'standart'
        }
    },
    data(){
        return {
            current_type_week: 'верхняя',
            week_number: '20'
        }
    }
}
</script>

<style scoped>

.week {
    max-width: 640px;
    padding: 5px;
    background-color:bisque;
}

.week__info {
    width: 60%;
    display: flex;
    justify-content: space-between;
    margin: auto;
}

.week__days {
    display: flex;
    justify-content: space-between;
    margin-top: 15px;
}
.week:has(.week__days.week__days--small) {
    max-width: 100%;
    margin: 0;
}
.week__days--medium,
.week__days--small {
    margin-top: 0;
}
</style>