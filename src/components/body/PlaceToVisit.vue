<template>
    <div class="place" :style="`background-image: url('${placeVicit}')`">
        <div class="gradient">
            <img :src="locationIcon" alt="location icon">
            <p>Arab Street <br> Singapour</p>
        </div>
    </div>
</template>

<script>
export default {
    name: "PlaceToVisit",
    data() {
        return {
            placeVicit: require('@/assets/img/singapour.jpg'),
            locationIcon: require('@/assets/icons/location_white.png'),
        }
    }
}
</script>

<style lang="scss">
    .place {
        width: 100%;
        height: 100%;
        background-size: cover;
        border-radius: 2rem;
        transition: all 0.3s;
        &:hover {
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.8);
        }
        .gradient {
            padding: 2rem;
            width: 100%;
            height: 100%;
            border-radius: 2rem;
            display: flex;
            background: rgb(0,0,0);
            background: linear-gradient(180deg, rgba(0,0,0,0.6) 0%, rgba(0,0,0,0.3) 30%, rgba(0,0,0,0.1) 50%, rgba(0,0,0,0) 66%, rgba(0,0,0,0) 0100%);
            img {
                width: 18px;
                height: 18px;
                margin-right: 0.5rem;
            }
            p {
                font-weight: 500;
                color: #fff;
            }
        }
    }
</style>