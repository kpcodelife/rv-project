<template>
    <header :class="{ 'isOpen': isMenuOpen }" class="vm-header">
        <nav class="vm-header-menu">
            <div v-for="link in headerLinks" :key="link.id" class="vm-header-menu-item">
                <a :href="link.linkTo">{{ link.name }}</a>
            </div>
        </nav>
        <div v-if="isMobile" @click="isMenuOpen = !isMenuOpen" :class="{ 'isOpen': isMenuOpen }"
            class="vm-header-hamburger">
            <span></span><span></span><span></span>
        </div>
    </header>
</template>

<script>
export default {
    name: "MainHeader",
    data() {
        return {
            isMobile: false,
            headerLinks: [
                {
                    id: 1,
                    name: 'Heading 1',
                    linkTo: 'https://wwww.google.com'
                },
                {
                    id: 2,
                    name: 'Heading 2',
                    linkTo: 'https://wwww.google.com'
                },
                {
                    id: 3,
                    name: 'Heading 3',
                    linkTo: 'https://wwww.google.com'
                },
            ],
            isMenuOpen: false
        }
    },
    methods: {
        updateMobileStatus() {
            this.isMobile = window.innerWidth <= 762;
        }
    },
    mounted() {
        this.updateMobileStatus();
        window.addEventListener('resize', this.updateMobileStatus);
    },
    beforeUnmount() {
        window.removeEventListener('resize', this.updateMobileStatus);
    }
}
</script>

<style lang="scss">
.vm-header {
    position: sticky;
    top: 0;
    background: rgb(255, 255, 255);
    background: linear-gradient(180deg, rgb(255, 255, 255, 1) 80%, rgb(236, 236, 236) 100%);
    display: flex;
    justify-content: center;
    align-items: center;
    height: 72px;
    width: 100%;
    transition: height 0.2s ease;
    border-bottom: 1px solid rgb(236, 236, 236);
    z-index: 99;

    &-hamburger {
        position: fixed;
        top: 12px;
        right: 12px;
        align-self: flex-start;
        justify-self: flex-end;
        width: 48px;
        height: 48px;
        display: flex;
        justify-content: center;
        flex-direction: column;
        gap: 4px;
        align-items: flex-end;
        padding: 10px;
        box-sizing: border-box;

        span {
            height: 3px;
            background-color: #1E1E1E;
            border-radius: 2px;

            &:nth-of-type(1) {
                width: 28px;
            }

            &:nth-of-type(2) {
                width: 24px;
            }

            &:nth-of-type(3) {
                width: 20px;
            }
        }

        &.isOpen {
            span {
                &:nth-of-type(1) {
                    width: 28px;
                }

                &:nth-of-type(2) {
                    width: 28px;
                }

                &:nth-of-type(3) {
                    width: 28px;
                }
            }

        }
    }

    &-menu {
        display: none;

        &-item {

            a {
                font-size: 20px;
                display: block;
                color: #1E1E1E;
                text-decoration: none;
                height: 48px;
                display: flex;
                align-items: center;
                padding: 0 32px;
                font-family: 'Roboto', sans-serif;
            }
        }
    }

    &.isOpen {
        height: 100lvh;

        @supports(not(height: 100lvh)) {
            min-height: 100vh;
            min-height: -webkit-fill-available;
        }

        .vm-header-menu {
            display: block;
        }
    }

    @media screen and (min-width: 762px) {
        &-hamburger {
            display: none;
        }

        &-menu {
            display: flex;
            gap: 64px;


            &-item {
                a {
                    position: relative;

                    &:after {
                        content: '';
                        display: block;
                        height: 2px;
                        width: 0px;
                        background-color: #1E1E1E;
                        position: absolute;
                        bottom: 4px;
                        left: 0;
                        transition: width 0.2s ease;
                    }
                }

                &:hover {
                    a {
                        &:after {
                            width: 100%;
                        }
                    }

                }
            }

        }
    }

}
</style>