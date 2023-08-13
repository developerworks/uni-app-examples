<template>

    <swiper class="swiper" circular :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval"
        :duration="duration">
        <swiper-item class="swiper-item" v-for="(image, index) in images" :key="index" @click="handleClick(index)">
            <img class="swiper-image" :src="image" :alt="index" />

        </swiper-item>
    </swiper>

</template>
<script>
    export default {
        data() {
            return {
                background: ['blue', 'red', 'green'],
                indicatorDots: true,
                autoplay: true,
                interval: 10000,
                duration: 1000,
                images: [
                    '/static/11.png',
                    '/static/22.png',
                    '/static/33.png'
                ],
                currentIndex: 0,
            }
        },
        methods: {
            changeIndicatorDots(e) {
                this.indicatorDots = !this.indicatorDots
            },
            changeAutoplay(e) {
                this.autoplay = !this.autoplay
            },
            intervalChange(e) {
                this.interval = e.detail.value
            },
            durationChange(e) {
                this.duration = e.detail.value
            },
            handleClick(index) {
                this.currentIndex = index;
                this.$router.push({
                    name: 'CarouselPage',
                    params: {
                        index: index
                    }
                });
            },
        }
    }
</script>

<style>
    .swiper {
        height: 300rpx;
    }

    .swiper-item {
        width: 100%;
        height: 400px;
    }

    .swiper-image {
        width: 100%;
        height: auto;
        top: 0;
        left: 0;
    }

    .uni-swiper {
        /* height: 166px; */
    }

    .swiper-item-image {
        height: 332rpx;
    }
</style>