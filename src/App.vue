<template>
    <div>
        <!-- For loop to iterate each item in the json file -->
        <div v-for="day in days" :key="day">
            <Holidays v-bind:holiday="day" />
        </div>
    </div>
</template>

<script>
// Import Json file
import holidays_json from "./assets/json/holidays.json";
// Import Components
import Holidays from "./components/Holidays.vue";

export default {
    name: "App",
    data() {
        // Return the json file as a object to loop (line: 3)
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
