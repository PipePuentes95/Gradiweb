<template>
    <div class="reviews">
        <div class="top-reviews">
            <div class="top-btn">
                <button>+</button> Top Reviews
            </div>
            <div class="reviews">
                <img src="https://randomuser.me/api/portraits/thumb/men/20.jpg" alt="random user">
                <img src="https://randomuser.me/api/portraits/thumb/women/20.jpg" alt="random user">
                <img src="https://randomuser.me/api/portraits/thumb/men/40.jpg" alt="random user">
                <button class="more-reviews">6+</button>
            </div>
        </div>
        <div class="locations">
            <div class="location-1" :style="`background-image: url('${museum}')`">
                <img :src="locationIcon" alt="">  <p>Art Science <br> Museum</p> 
            </div>
            <div class="location-2" :style="`background-image: url('${fountain}')`">
                <img :src="locationIcon" alt=""><p>Fountain <br> of Wealth</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Reviews",
    data() {
        return {
            museum: require('@/assets/img/museum.jpg'),
            fountain: require('@/assets/img/fountain.jpg'),
            locationIcon: require('@/assets/icons/location_white.png'),
        }
    }
}
</script>

<style lang="scss">
@import '../../_vars.scss';
     .reviews{
        .top-reviews {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.5rem;
            .top-btn {
                button {
                    color: $purple-light;
                    font-size: 20px;
                    border: none;
                    background: none;
                    margin-right: 0.5rem;
                }
            }
            .reviews {
                display: flex;
                img {
                    height: 35px;
                    margin-left: 0.3rem;
                    border-radius: 0.5rem;
                }
                button {
                    padding: 0 0.5rem;
                    display: inline;
                    background: $purple-light;
                    color: #fff;
                    font-size: 16px;
                    border-radius: 0.5rem;
                    border: none;
                    margin-left: 0.3rem;
                }
            }
        }
        .locations {
            width: 100%;
            height: 100%;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            .location-1, .location-2 {
                width: 100%;
                background-size: cover;
                padding: 2rem;
                display: flex;
                transition: all 0.3s;
                &:hover {
                    box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.8);
                }
                    img {
                        width: 18px;
                        height: 18px;
                        margin-right: 0.5rem;
                    }
                    p {
                        font-weight: bold;
                        color: #fff;
                    }
                
            }
            .location-1 {
                height: 40%;
                border-radius: 1.5rem;
                background-position: center;
            }
            .location-2 {
                height: 50%;
                border-radius: 2rem;
                background-position: bottom;
            }
        }
    }
</style>