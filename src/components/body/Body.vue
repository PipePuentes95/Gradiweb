<template>
    <div class="container">
        <div class="col next-days">
            <h3><span>3 Days</span> Forecast</h3>
            <Forecast
                v-for="(current, index) in forecast"
                :key="index"
                :current="current"
                :day="daysName[today.getDay() + index]"
            />
        </div>
        <div class="col next-days">
            <h3><span>Place to</span> visit</h3>
            <PlaceToVisit />
        </div>
        <Reviews class="col next-days" />
        <TempParis :paris="paris" :lyon="lyon" />
    </div>
</template>

<script>
import Forecast from './Forecast';
import PlaceToVisit from './PlaceToVisit';
import Reviews from './Reviews';
import TempParis from './TempParis';
export default {
    name:"Body",
    components: {
        Forecast,
        PlaceToVisit,
        Reviews,
        TempParis
    },
    props: {
        forecast: Array,
        paris: Object,
        lyon: Object
    },
    data() {
        return {
            today: new Date(),
            daysName: ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday","Sunday", "Monday", "Tuesday", "Wednesday"]
        }
    }
}
</script>

<style lang="scss">
    @import '../../_vars.scss';
    .container {
        width: 100%;
        height: 50vh;
        display: flex;
        padding: 0 2rem 2rem;
        .col {
            padding: 1rem;
            width: 25%;
            height: 100%;
        }
        .next-days {
            display: flex;
            flex-direction: column;
            h3 {
                font-weight: 300;
                font-size: 1.8rem;
                margin-bottom: 1.5rem;
                span {
                    font-weight: bold;
                }
            }
        }
    }
    @media (max-width: 1300px) {
        .container {
            height: 50vh;
            flex-wrap: wrap;
            .col {
                width: 50%;
                height: 70%;
            }
        }
    }
    @media (max-width: 800px) {
        .container {
            height: 80vh;
            padding: 0 1rem 1rem;
            .col {
                width: 100%;
                height: 70%;
            }
        }
    }
</style>