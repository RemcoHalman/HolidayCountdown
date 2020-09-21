<template>
    <div>
        <section
            id="holiday"
            v-bind:style="{
                backgroundColor: holiday.defaultBG,
            }"
        >
            <div>
                <h1>{{ holiday.name }}</h1>
                <p id="time">
                    Datum: {{ holiday.day }}-{{ holiday.month }}-{{
                        holiday.year
                    }}
                </p>
                <p>
                    Time until:
                    {{ ticker(holiday.year, holiday.month, holiday.day) }}
                </p>
            </div>
        </section>
    </div>
</template>

<script>
export default {
    name: "Holidays",
    props: {
        holiday: JSON,
    },
    data() {
        return {
            time: "",
        };
    },
    computed: {},
    methods: {
        refactor_time: function(time) {
            var days = Math.floor(time / (1000 * 60 * 60 * 24));
            var hours = Math.floor(
                (time % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60)
            );
            var minutes = Math.floor((time % (1000 * 60 * 60)) / (1000 * 60));
            var seconds = Math.floor((time % (1000 * 60)) / 1000);
            return days + "d " + hours + "h " + minutes + "m " + seconds + "s ";
        },
        ticker: function(year, month, day) {
            var data_text = year + "-" + month + "-" + day;
            var date = new Date(data_text).getTime();
            var now = new Date().getTime();
            var time = date - now;
            var days_until = this.refactor_time(time);
            // console.log(days_until);
            return days_until;
        },
    },
};
</script>

<style lang="scss"></style>
