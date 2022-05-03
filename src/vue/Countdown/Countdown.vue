<template>
    <div class="banner">
        <div class="container">
            <div class="row row--countdown">
            
                <h1>{{ title }}</h1>
                <div class="countdown">
                    <CountdownUnit v-for="(item, index) in timeDifferenceObj" :key='index' :value='item' :unit='index' />
                </div>

            </div>
        </div>
    </div>
</template>

<script>
import CountdownUnit from "../CountdownUnit/CountdownUnit.vue"; // Made a seperate component for each countdown unit

export default {
    components: {
        CountdownUnit
    },

    data() {
        return {
            timeDifferenceObj: {
                days: 0,
                hours: 0,
                min: 0,
                sec: 0
            }
        }
    },

    props: {
        title: {
            type: String
        }
    },
    
    methods: {
        calculateTimeDifference(date1, date2) {
            const HOURSINADAY = 24;
            const MINUTESINANHOUR = 60;
            const SECONDSINAMINUTE = 60;

            const difference = (date2 - date1) / 1000; // subtract dates and shave off the miliseconds

            // convert x amount of seconds to days, hours, mins, sec
            this.timeDifferenceObj.days = Math.floor(difference / ( SECONDSINAMINUTE * MINUTESINANHOUR * HOURSINADAY ));
            let restDays = difference % ( SECONDSINAMINUTE * MINUTESINANHOUR * HOURSINADAY );
            this.timeDifferenceObj.hours = Math.floor(restDays / ( SECONDSINAMINUTE * MINUTESINANHOUR ));
            let restHours = restDays % ( SECONDSINAMINUTE * MINUTESINANHOUR );
            this.timeDifferenceObj.min = Math.floor(restHours / ( SECONDSINAMINUTE ));
            this.timeDifferenceObj.sec = Math.floor(restHours % ( SECONDSINAMINUTE ));
        }
    },

    mounted() {
        setInterval(() => {
            this.calculateTimeDifference( Date.now(), new Date('November 22, 2022') ); // black friday this year is 22/25th of november
        }, 1000);
    }

};
</script>

<style lang="scss" scoped>
    @import './Countdown.scss';
</style>