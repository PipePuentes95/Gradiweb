<template>
    <header>
        <div class="bg-img" :style="`background-image: url('${bogImg}')`">
            <h2 class="location-title">
                <img :src="locationIcon" alt="location icon">
                Bogotá
            </h2>
            <img class="map" :src="mapIcon" alt="map">
        </div>
        <MainWeather :current="current" />
    </header>
</template>

<script>
import MainWeather from './MainWeather';
export default {
    name:'Header',
    props: {
        current: Object
    },
    components: {
        MainWeather
    },
    data() {
        return {
            bogImg: require('@/assets/img/bogota_bg.jpg'),
            locationIcon: require('@/assets/icons/location_purple.png'),
            mapIcon: require('@/assets/img/map_v1.png')
        }
    }
}
</script>
<style lang="scss">
    @import '../../_vars.scss';
    header {
        width: 100%;
        height: 50vh;
        display: flex;
        justify-content: center;
        align-items: center;
        padding: 3rem;
        position: relative;
        .bg-img {
            width: 100%;
            height: 100%;
            border-radius: 2rem;
            background-size: cover;
            padding: 6rem 8rem;
            .location-title {
                display: flex;
                color: $purple-light;
                margin-bottom: 1rem;
                img {
                    max-height: 1.8rem;
                    margin-right: 0.5rem;
                }
            }
            .map {
               width: 150px;
            }
        }
    }
</style>