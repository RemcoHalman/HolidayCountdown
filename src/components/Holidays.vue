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
    methods: {
        ticker: function(year, month, day) {
            var data_text = year + "-" + month + "-" + day;
            var date = new Date(data_text).getTime();
            var now = new Date().getTime();
            var t = date - now;
            var days = Math.floor(t / (1000 * 60 * 60 * 24));
            var hours = Math.floor(
                (t % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60)
            );
            var minutes = Math.floor((t % (1000 * 60 * 60)) / (1000 * 60));
            var seconds = Math.floor((t % (1000 * 60)) / 1000);
            var days_until =
                days + "d " + hours + "h " + minutes + "m " + seconds + "s ";
            // console.log(days_until);
            return days_until;
        },
    },
};
</script>

<style lang="scss"></style>
