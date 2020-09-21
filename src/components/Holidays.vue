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
        // Get passed prop and setting it to a variable
        holiday: JSON,
    },
    data() {
        return {
            // Initialising time as a empty string
            time: "",
        };
    },
    computed: {},
    methods: {
        refactor_time: function(time) {
            // Calculate the days
            var days = Math.floor(time / (1000 * 60 * 60 * 24));
            // Calculate the hours in above day
            var hours = Math.floor(
                (time % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60)
            );
            // Calculate the minutes in above hour
            var minutes = Math.floor((time % (1000 * 60 * 60)) / (1000 * 60));
            // Calculate the seconds in above minute
            var seconds = Math.floor((time % (1000 * 60)) / 1000);
            // Return data to the template
            return days + "d " + hours + "h " + minutes + "m " + seconds + "s ";
        },
        ticker: function(year, month, day) {
            var data_text = year + "-" + month + "-" + day;
            // Get the json date entered
            var date = new Date(data_text).getTime();
            // Get the current time and date
            var now = new Date().getTime();
            // Calculate the difference
            var time = date - now;
            // Running the format function
            var days_until = this.refactor_time(time);
            // Returns the formated time until
            return days_until;
        },
    },
};
</script>

<style lang="scss"></style>
