<template>
    <div class="forecast">
        <div class="icon">
            <img :src="require(`@/assets/icons/${ current.weather[0].icon }.png`)" alt="forecast icon">
        </div>
        <div class="day">
            <h4>{{ day }}</h4>
            <p>{{ current.weather[0].main}}</p>
        </div> 
        <div class="temp">
            <span>{{ Math.floor(current.temp.max - 273.15) }}<sup>°c</sup> </span>
            <span>/</span>
            <span>{{ Math.floor(current.temp.min - 273.15) }}<sup>°c</sup></span>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        current: Object,
        day: String
    }
}
</script>

<style lang="scss">
    @import '../../_vars.scss';
    .forecast {
        width: 100%;
        height: 100%;
        border: 0.1px solid #c1d1e0;
        border-radius: 2rem;
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between ;
        align-items: center;
        margin-top: 0.5rem;
        transition: all 0.3s;
        &:hover {
            box-shadow: 0px 0px 6px rgba(0, 0, 0, 0.3);
            .temp {
                background: $purple-light;
                color: #fff;
            }
        }
        .icon {
            width: 25%;
            padding-left: 1rem;
            img {
                width: 50px;
            }
        }
        .day {
            width: 35%;
            h4 {
                font-size: 18px;
                color: $text-purple-dark-one;
            }
            p {
                color: $text-gray-light;
            }
        }
        .temp {
            background: $gray-light;
            width: 40%;
            height: 100%;
            border-radius: 2rem;
            display: flex;
            justify-content: center;
            align-items: center;
            font-weight: bold;
            font-size: 25px;
            transition: all 0.3s;
            sup {
                font-size: 12px;
                font-weight: 300;
            }
        }
    }
     @media (max-width: 800px) {
    }
</style>