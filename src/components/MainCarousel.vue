<template>
    <div class="vm-carousel-container">
        <button @click="prevSlide" class="vm-carousel-button-prev"><span class="sr-only">Prev</span><img
                :src="require(`@/assets/chevron_left.svg`)" alt=""></button>
        <button @click="nextSlide" class="vm-carousel-button-next"><span class="sr-only">Next</span><img
                :src="require(`@/assets/chevron_right.svg`)" alt=""></button>

        <div class="vm-carousel" ref="carousel" @scroll="handleScroll">
            <div v-for="(slide, index) in carouselSlides" :key="slide.id" class="vm-carousel-slide"
                :style="{ scrollSnapAlign: index === currentSlide ? 'start' : 'none' }">

                <img :src="require(`@/assets/images/${slide.imageLink}`)" :alt="slide.text">

                <div class="vm-carousel-slide-text">
                    <p>{{ slide.text }}</p>
                </div>
            </div>
        </div>

        <div class="vm-carousel-pagination">
            <button v-for="(slide, index) in carouselSlides" :key="slide.id" :class="{ 'active': currentSlide === index }"
                @click="goToSlide(index)">
                <span class="sr-only">View Slide {{ index + 1 }}</span>
            </button>
        </div>
    </div>
</template>

<script>
export default {
    name: "MainCarousel",
    data() {
        return {
            currentSlide: 0,
            carouselSlides: [
                {
                    id: 1,
                    text: "AI Meets Mother Nature",
                    imageLink: 'Mountains-1.png'
                },
                {
                    id: 2,
                    text: "AI Meets Mother Nature",
                    imageLink: 'Mountains-2.png'
                },
                {
                    id: 3,
                    text: "AI Meets Mother Nature",
                    imageLink: 'Mountains-3.png'
                },
            ]
        }
    },
    methods: {
        handleScroll(event) {
            this.currentSlide = Math.round(event.target.scrollLeft / event.target.clientWidth);
        },
        prevSlide() {
            if (this.currentSlide === 0) {
                this.goToSlide(this.carouselSlides.length - 1);
            } else {
                this.goToSlide(this.currentSlide - 1);
            }
        },
        nextSlide() {
            if (this.currentSlide === this.carouselSlides.length - 1) {
                this.goToSlide(0);
            } else {
                this.goToSlide(this.currentSlide + 1);
            }
        },
        goToSlide(index) {
            this.currentSlide = index;
            this.$nextTick(() => {
                this.$refs.carousel.scrollLeft = index * this.$refs.carousel.clientWidth;
            });
        }
    }
}
</script>

<style lang="scss" scoped>
.vm-carousel-container {
    position: relative;
    min-width: 100%;

    .vm-carousel {
        display: flex;
        width: 100%;
        height: 300px;
        overflow-x: auto;
        scroll-snap-type: x mandatory;

        &-slide {
            flex: 0 0 100%;
            min-width: 100%;
            height: 300px;
            position: relative;

            img {
                width: 100%;
                height: 100%;
                object-fit: cover;
                display: block;
            }

            &-text {
                position: absolute;
                top: 50%;
                left: 50%;
                transform: translate(-50%, -50%);
                color: $white;
                font-size: 18px;
                font-family: "Montserrat", sans-serif;
            }

        }

        &-button {

            &-prev,
            &-next {
                position: absolute;
                top: 50%;
                transform: translateY(-50%);
                padding: 10px;
                background-color: transparent;
                border: none;
                outline: 2px solid $white;
                cursor: pointer;
                border-radius: 50%;
                width: 32px;
                height: 32px;
                display: flex;
                align-items: center;
                justify-content: center;
                z-index: 10;

                img {
                    display: block;
                    height: 16px;
                }

            }

            &-prev {
                left: 16px;
            }

            &-next {
                right: 16px;
            }
        }

        &-pagination {
            position: absolute;
            left: 50%;
            bottom: 16px;
            transform: translateX(-50%);
            display: flex;
            gap: 12px;

            button {
                width: 8px;
                height: 8px;
                border-radius: 50%;
                cursor: pointer;
                border: none;
                background-color: transparent;
                outline: 1px solid $white;
                transition: background-color ease 0.2s;

                &.active {
                    background-color: $white;
                    outline: 3px solid $white;
                    outline-offset: -1px;
                }
            }
        }

        @media screen and (min-width: 762px) {
            height: 500px;

            &-slide {
                height: 500px;

                &-text {
                    font-size: 32px;
                }
            }

            &-button {

                &-prev,
                &-next {
                    transition: background-color 0.2s ease;

                    &:hover {
                        outline: 3px solid $white;
                        outline-offset: -1px;
                        background-color: $white;

                        img {
                            mix-blend-mode: exclusion;
                        }
                    }
                }

                &-prev {
                    left: 32px;
                }

                &-next {
                    right: 32px;
                }
            }

            &-pagination {
                bottom: 40px;

                button {
                    &:hover {
                        outline: 2px solid $white;

                    }
                }
            }
        }

        @media screen and (min-width: 1024px) {
            &-slide {

                &-text {
                    font-size: 48px;
                }
            }

            &-button {

                &-next,
                &-prev {
                    width: 44px;
                    height: 44px;
                }

                img {
                    height: 20px;
                }
            }

        }
    }
}

.sr-only {
    position: absolute;
    width: 1px;
    height: 1px;
    padding: 0;
    margin: -1px;
    overflow: hidden;
    clip: rect(0, 0, 0, 0);
    white-space: nowrap;
    border: 0;
}

/* Optional: Adds a smooth scroll effect */
.vm-carousel::-webkit-scrollbar {
    display: none;
}

.vm-carousel {
    -ms-overflow-style: none;
    scrollbar-width: none;
}
</style>