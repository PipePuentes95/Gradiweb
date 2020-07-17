<template>
    <div class="col next-days international">
        <div class="card first">
            <div class="card-body">
                <div class="card-img">
                    <img
                        v-if="weatherLyon.icon"
                        :src="require(`@/assets/icons/${ weatherLyon.icon }.png`)"
                        alt=""
                    >
                </div>
                <div class="card-temp" v-if="tempLyon">
                    {{ Math.floor(tempLyon.temp - 273.15) }}<sup>°c</sup>
                </div>
                <div class="card-info">
                    <span>{{ lyon.name }}</span>
                    <br/>
                    Francia
                </div>
            </div>
            <div class="card-footer">
                <p v-if="tempLyon.humidity">humidity {{ tempLyon.humidity }} %</p>
                <p>Nortwest</p>
                <p v-if="windLyon.speed">{{ windLyon.speed }} km/h</p>
            </div>
        </div>
        <div class="card">
            <div class="card-body">
                <div class="card-img">
                    <img
                        v-if="weatherParis.icon"
                        :src="require(`@/assets/icons/${ weatherParis.icon }.png`)"
                        alt=""
                    >
                </div>
                <div class="card-temp" v-if="tempParis">
                    {{ Math.floor(tempParis.temp - 273.15) }}<sup>°c</sup>
                </div>
                <div class="card-info">
                    <span>{{ paris.name }}</span>
                    <br/>
                    Francia
                </div>
            </div>
            <div class="card-footer">
                <p v-if="tempParis.humidity">humidity {{ tempParis.humidity }} %</p>
                <p>west</p>
                <p v-if="windParis.speed">{{ windParis.speed }} km/h</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "TempParis",
    props: {
        paris: Object,
        lyon: Object
    },
    computed: {
        tempParis() {
            return this.paris.main ? this.paris.main : false
        },
        weatherParis() {
            return this.paris.weather ? this.paris.weather : false
        },
        windParis() {
            return this.paris.wind ? this.paris.wind : false
        },
        tempLyon() {
            return this.paris.main ? this.paris.main : false
        },
        weatherLyon() {
            return this.paris.weather ? this.paris.weather : false
        },
        windLyon() {
            return this.lyon.wind ? this.lyon.wind : false
        },
    }
}
</script>

<style lang="scss">
    @import '../../_vars.scss';
    .international {
        .card {
            height: 100%;
            margin-top: 2rem;
            border-radius: 2rem;
            border: 0.1px solid #c1d1e0;
            color: $text-purple-dark-one;
            transition: all 0.3s;
            &:hover {
                box-shadow: 0px 0px 6px rgba(0, 0, 0, 0.5);
            }
            &.first {
                margin-top: 0;
            }
            .card-body {
                height: 60%;
                display: flex;
                align-items: center;
                .card-img {
                    width: 30%;
                    height: 100%;
                    background: $purple-light;
                    border-radius: 2rem;
                    position: relative;
                    img {
                        position: absolute;
                        left: 50%;
                        top: 50%;
                        transform: translate(-50%, -50%);
                        width: 60px;
                    }
                }
                .card-temp {
                    width: 25%;
                    text-align: center;
                    font-size: 36px;
                    font-weight: bold;
                    sup {
                        font-size: 16px;
                        font-weight: 300;
                        color: $purple-light;
                    }
                }
                .card-info {
                    width: 45%;
                    padding-right: 1rem;
                    span {
                        font-weight: bold;
                        font-size: 20px;
                    }
                }
            }
            .card-footer {
                display: flex;
                height: 40%;
                justify-content: space-around;
                align-items: center;
                p {
                    color: $text-gray-light;
                    font-size: 14px;
                }
            }
        }
    }
</style>