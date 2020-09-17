<template>
    <div>
        <div v-for="day in days" :key="day">
            <Holidays v-bind:holiday="day" />
        </div>
    </div>
</template>

<script>
import holidays_json from "./assets/json/holidays.json";
import Holidays from "./components/Holidays.vue";

export default {
    name: "App",
    data() {
        return { days: holidays_json };
    },
    components: {
        Holidays,
    },
};
</script>

<style lang="scss">
@import "@/assets/scss/main";
</style>
