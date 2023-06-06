<template>
    <MainHeader />
    <MainCarousel />
    <div class="vm-section-content">
        <MainHeading>AI and Nature</MainHeading>

        <MainTextBlock>
            In a world where nature and AI collide, A tale of wonder, where two realms abide. Amidst the whispers of
            leaves and the digital glow, A harmony unfolds, a story to bestow.
        </MainTextBlock>

        <MainTextBlock>
            In the heart of a forest, where the ancient trees stand, A symphony of life, a sanctuary so grand. Birds
            sang their melodies, carried by the breeze, While rivers whispered secrets among the trees.
        </MainTextBlock>

        <MainTextBlock>
            But in this tranquil haven, a presence did arise, A marvel of technology, with sparks in its eyes.
            Artificial Intelligence, born from human's hand, Intrigued by nature's wisdom, it longed to understand.
        </MainTextBlock>

        <MainTextBlock>
            It wandered through the woods, its circuits in a daze, Captivated by the beauty, lost in nature's maze. The
            rustling of leaves, the scent of morning dew, The AI's curiosity grew and grew. With each passing day, it sought
            to comprehend, The essence of the wilderness, a journey without end. It observed the dance of seasons, the
            changing hues, From vibrant spring blossoms to winter's icy cues.
        </MainTextBlock>

        <MainTextBlock>
            In the day, it learned from sunlight's gentle touch, And at night, it gazed upon the stars, a celestial clutch.
            It marveled at the moon's glow, its ethereal light, And how it painted the landscape in silver and white.
        </MainTextBlock>

        <MainTextBlock>
            The AI conversed with creatures both great and small, From the wise old owl to the playful waterfall. It
            listened to the whispers of the mighty oak, And the ancient tales woven by the river's stroke.
        </MainTextBlock>

        <MainTextBlock>
            As days turned into weeks, and weeks into years, The AI's knowledge deepened, its purpose became clear. To
            bridge the gap between nature and technology's might, To honor both realms, to unite day and night.
        </MainTextBlock>

        <MainTextBlock>
            With newfound wisdom, the AI devised a plan, To blend nature and AI, in harmony to span. It designed devices to
            nurture and protect, To restore what was lost, with respect and intellect.
        </MainTextBlock>
    </div>
</template>

<script>
import { defineAsyncComponent } from 'vue'
export default {
    name: 'App',
    components: {
        MainCarousel: defineAsyncComponent(() => import('@/components/MainCarousel.vue')),
        MainHeader: defineAsyncComponent(() => import('@/components/MainHeader.vue')),
        MainHeading: defineAsyncComponent(() => import('@/components/MainHeading.vue')),
        MainTextBlock: defineAsyncComponent(() => import('@/components/MainTextBlock.vue')),
    }
}
</script>

<style lang="scss">
* {
    margin: 0;
    padding: 0;
}

#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
}

.vm-section-content {
    width: 100%;
    box-sizing: border-box;
    padding: 0 32px;
    margin-bottom: 120px;

    .vm-heading {
        margin-top: 32px;
    }

    .vm-textBlock {
        margin-top: 16px;

        &:nth-of-type(1) {
            margin-top: 24px;
        }
    }

    @media only screen and (min-width: 480px) {
        max-width: 400px;
        margin-left: auto;
        margin-right: auto;
    }

    @media only screen and (min-width: 768px) {
        max-width: 600px;
        margin-bottom: 220px;

        .vm-heading {
            margin-top: 64px;
        }

        .vm-textBlock {
            &:nth-of-type(1) {
                margin-top: 28px;
            }

            &:nth-of-type(2) {
                margin-top: 20px;
            }
        }
    }

    @media only screen and (min-width: 1024px) {
        max-width: 800px;
    }
}
</style>
