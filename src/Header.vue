<template>
    <header :class="['MainHeader', {'is-menuOpened': expanded}]">
        <div class="MainHeader__mobile">
            <div class="MainHeader__title">
                <button class="MainHeader__icon" @click.prevent="expanded = true">
                    <svg viewBox="0 0 30 30" class="SvgIcon MainHeader__burger">
                        <path d="M28.75 2.5H1.25a1.25 1.25 0 0 0 0 2.5h27.5a1.25 1.25 0 0 0 0-2.5zM1.25 16.25h17.5a1.25 1.25 0 0 0 0-2.5H1.25a1.25 1.25 0 0 0 0 2.5zM23.75 25H1.25a1.25 1.25 0 0 0 0 2.5h22.5a1.25 1.25 0 0 0 0-2.5z"></path>
                    </svg>
                    <span class="MainHeader__menu">Izbornik</span>
                </button>
                <a title="Renault Hrvatska" class="MainHeader__text" href="/">Renault Hrvatska</a>
            </div>
            <a title="Renault logo" class="Link" data-track="click" data-track-button-text="logo-renault-header"
               data-track-destination="/" data-track-location-in-page="primary-nav" data-track-event="navigationClick"
               href="/">
                <picture class="MainHeader__logo is-contained">
                    <source srcset="https://cdn.group.renault.com/ren/si/home-page/legal-part/fthcfgjhfjg.png.asset.png/98671d15cb.png"
                            media="(min-width: 1024px)" type="image/png">
                    <img src="https://cdn.group.renault.com/ren/si/home-page/legal-part/fthcfgjhfjg.png.asset.png/98671d15cb.png"
                         alt="Renault Hrvatska" class="PictureElement__imgDefault">
                    <noscript>
                        <img src="https://cdn.group.renault.com/ren/si/home-page/legal-part/fthcfgjhfjg.png.asset.png/98671d15cb.png"
                            alt="Renault Hrvatska"/>
                    </noscript>
                </picture>
            </a>
        </div>
        <div class="MainHeader__desktop">
            <div class="MainHeader__content">
                <div class="MainHeader__top">
                    <div class="HeaderSites">
                        <a title="Renault Hrvatska" class="HeaderSites__site is-active" href="/">
                            <div class="HeaderSites__text">
                                <div class="HeaderSites__title"><span class="HeaderSites__label">Renault Hrvatska</span>
                                </div>
                            </div>
                            <span class="HeaderSites__text HeaderSites__icon">
                                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 30 30" class="HeaderSites__iconSvg">
                                    <path d="M1.822 7.527a1.058 1.058 0 0 0-1.46 1.532l14.384 13.707L29.624 9.071a1.059 1.059 0 0 0-1.432-1.558l-13.42 12.354-12.95-12.34z"></path>
                                </svg>
                            </span>
                        </a>
                        <a
                                v-for="(navigationItem, itemIndex) in topNavigation"
                                :key="itemIndex"
                                :title="navigationItem.title"
                                class="HeaderSites__site"
                                :href="navigationItem.url"
                                :target="Number(navigationItem.target) === 1 ? '_blank' : undefined">

                            <div class="HeaderSites__text">
                                <div class="HeaderSites__title"><span class="HeaderSites__label">{{ navigationItem.title }}</span>
                                </div>
                            </div>
                        </a>
                    </div>
                    <a title="Renault logo" class="MainHeader__brand" data-track="click"
                       data-track-button-text="logo-renault-header" data-track-destination="/"
                       data-track-location-in-page="primary-nav" data-track-event="navigationClick" href="/">
                        <picture class="MainHeader__logo is-contained">
                            <source srcset="https://cdn.group.renault.com/ren/si/home-page/legal-part/fthcfgjhfjg.png.asset.png/98671d15cb.png"
                                    media="(min-width: 1024px)" type="image/png">
                            <img src="https://cdn.group.renault.com/ren/si/home-page/legal-part/fthcfgjhfjg.png.asset.png/98671d15cb.png"
                                 alt="Renault Hrvatska" class="PictureElement__imgDefault">
                            <noscript><img
                                    src="https://cdn.group.renault.com/ren/si/home-page/legal-part/fthcfgjhfjg.png.asset.png/98671d15cb.png"
                                    alt="Renault Hrvatska"/></noscript>
                        </picture>
                    </a>
                </div>
                <div class="MainHeader__bottom">
                    <div class="MainMenu is-visible">
                        <ul class="MainMenu__navList">
                            <li class="MainMenuEntry MainMenuEntry_home">
                                <a title="" class="MainMenuEntry__link" data-track="click" data-track-button-text="logo"
                                   data-track-destination="/" data-track-location-in-page="primary-nav"
                                   data-track-event="navigationClick" href="/">
                                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 30 30"
                                         class="SvgIcon MainMenuEntry__linkicon">
                                        <path d="M25.549 29.989h-8.383V19.212c.037-.839-.101-1.398-.408-1.72-.317-.335-.905-.502-1.744-.502-1.68 0-2.347.63-2.379 2.244v10.6H4.483V15.76h2.46v11.613h3.231V19.21c.062-2.985 1.826-4.68 4.84-4.68 1.538 0 2.721.426 3.526 1.265.787.824 1.154 1.995 1.085 3.474l.002 8.26h3.462V16.065h2.46v13.924zM1.609 15.758l-1.631-1.84L15.67.011l14.352 13.946-1.715 1.764L15.594 3.367 1.609 15.758z"></path>
                                    </svg>
                                </a>
                            </li>

                            <MainMenuEntry
                                    v-for="(navigationItem, itemIndex) in mainNavigation"
                                    :key="itemIndex"
                                    :item="navigationItem"/>
                        </ul>
                    </div>
                    <div class="SearchLink">
                        <button class="SearchLink__button" data-track="click" data-track-button-text="Pretraga"
                                data-track-destination="/pretraga.html" data-track-location-in-page="primary-nav"
                                data-track-event="navigationClick">
                            <div class="SearchLink__icon">
                                <svg viewBox="0 0 30 30" class="SearchLink__iconSvg">
                                    <path d="M29.251 27.717l-6.473-6.473c1.952-2.245 3.145-5.165 3.145-8.355 0-7.028-5.75-12.778-12.779-12.778C6.116.111.366 5.861.366 12.889s5.75 12.778 12.778 12.778c2.93 0 5.631-1.01 7.793-2.685l6.524 6.524c.256.256.511.383.895.383.383 0 .639-.128.895-.383a1.236 1.236 0 0 0 0-1.789zm-26.329-14.7c0-5.622 4.6-10.223 10.223-10.223s10.223 4.6 10.223 10.223-4.6 10.223-10.223 10.223c-5.623-.001-10.223-4.601-10.223-10.223z"></path>
                                </svg>
                            </div>
                            <div class="SearchLink__text">Pretraga</div>
                        </button>
                    </div>
                    <div class="HeaderButtons">
                        <a title="Pronađite nas" class="HeaderButtons__button" href="/koncesionari.html">
                            <div class="HeaderButtons__icon">
                                <svg viewBox="0 0 30 30" class="HeaderButtons__iconSvg">
                                    <path d="M17.996 11.316c0-1.842-1.156-3-2.996-3s-2.996 1.157-2.996 3c0 1.841 1.156 3 2.996 3s2.996-1.158 2.996-3m1.788 0c0 2.684-2.05 4.738-4.784 4.738S10.216 14 10.216 11.316c0-2.738 2.05-4.738 4.784-4.738s4.784 2.001 4.784 4.738m4.574-.526c0-5.316-3.785-9-9.358-9s-9.358 3.684-9.358 9c0 4.789 3.523 11.42 9.358 17.474 5.835-6.054 9.358-12.685 9.358-17.474m-20.608 0C3.75 4.318 8.271 0 15 0s11.25 4.316 11.25 10.79c0 5.315-3.995 12.737-10.304 19.21h-1.892C7.745 23.526 3.75 16.105 3.75 10.79"></path>
                                </svg>
                            </div>
                            <div class="HeaderButtons__text">Pronađite nas</div>
                        </a>
                        <a title="Probna vožnja" class="HeaderButtons__button"
                           href="/obratite-nam-se/vozila-probna-voznja.html">
                            <div class="HeaderButtons__icon">
                                <svg viewBox="0 0 30 30" class="HeaderButtons__iconSvg">
                                    <path d="M8.783 10.209c-2.814 0-3.345.228-5.779 2.395-1.444 1.255-1.596 1.597-1.596 3.536 0 .951.342 1.445 1.065 1.597l.722.152-.266 1.255-.533-.114C.76 18.688.075 17.851.075 16.254v-.19c0-2.357.191-2.776 1.978-4.373 2.698-2.395 3.573-2.776 6.729-2.776h3.766c3.232 0 4.753.342 6.881 1.521l3.84 2.129 2.928.456c2.433.38 3.728 1.635 3.728 3.65 0 .951-.266 1.787-.762 2.471l-1.063-.76c.379-.57.493-.989.493-1.711 0-1.369-.987-2.167-3.002-2.471l-2.928-.418-3.84-2.167c-2.053-1.179-3.08-1.407-6.274-1.407l-3.766.001zm13.043 8.214c0-1.521 1.141-2.662 2.698-2.662 1.559 0 2.7 1.141 2.7 2.662s-1.141 2.662-2.7 2.662c-1.063 0-1.939-.532-2.395-1.369H9.202c-.456.836-1.332 1.369-2.395 1.369-1.559 0-2.7-1.141-2.7-2.662s1.141-2.662 2.7-2.662 2.698 1.141 2.698 2.662h12.321zM6.807 17.015c-.874 0-1.445.57-1.445 1.407 0 .836.57 1.407 1.445 1.407s1.445-.57 1.445-1.407-.571-1.407-1.445-1.407m17.717 0c-.874 0-1.443.57-1.443 1.407 0 .836.569 1.407 1.443 1.407.876 0 1.445-.57 1.445-1.407s-.569-1.407-1.445-1.407"></path>
                                </svg>
                            </div>
                            <div class="HeaderButtons__text">Probna vožnja</div>
                        </a>
                        <a href="https://onlineponuda.renault.hr/" title="Online ponuda" class="HeaderButtons__button"
                           rel="noopener">
                            <div class="HeaderButtons__icon">
                                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 48 48"
                                     class="HeaderButtons__iconSvg">
                                    <path d="M36.049 38.278c0-1.445-.951-2.43-2.344-2.43-1.398 0-2.349.985-2.349 2.43 0 1.444.951 2.43 2.349 2.43 1.393 0 2.344-.986 2.344-2.43m2.156 0c0 2.56-1.966 4.596-4.5 4.596-2.54 0-4.503-2.035-4.503-4.596s1.964-4.597 4.503-4.597c2.534 0 4.5 2.036 4.5 4.597m-15.664 0c0-1.445-.95-2.43-2.346-2.43-1.393 0-2.344.985-2.344 2.43 0 1.444.951 2.43 2.344 2.43 1.395 0 2.346-.986 2.346-2.43m2.157 0c0 2.56-1.966 4.596-4.503 4.596-2.534 0-4.502-2.035-4.502-4.596s1.968-4.597 4.502-4.597c2.537 0 4.503 2.036 4.503 4.597m-6.72-10.835h21.495l2.539-14.12H15.568l-.19-2.231H44.8l-3.424 18.583H17.912c-3.741 0-5.263-1.379-5.705-5.124L10.305 8.465c-.19-1.576-.952-2.232-2.54-2.232H3.2V4h4.566c3.36 0 4.566 1.114 4.946 4.465l1.776 16.154c.19 1.97 1.27 2.824 3.49 2.824"></path>
                                </svg>
                            </div>
                            <div class="HeaderButtons__text">Online ponuda</div>
                        </a>
                        <a title="MY Renault" class="HeaderButtons__button" href="/otkrijte-my-renault.html">
                            <div class="HeaderButtons__icon">
                                <svg viewBox="0 0 30 30" class="HeaderButtons__iconSvg">
                                    <path d="M15 13.234c3.434 0 5.403-2.27 5.403-5.449S18.434 2.337 15 2.337s-5.404 2.27-5.404 5.449 1.97 5.448 5.404 5.448zM4.193 29.429H2.375v-2.623c0-7.012 2.929-11.553 8.333-13.016-1.868-1.261-2.929-3.431-2.929-6.003 0-4.187 2.778-7.214 7.222-7.214s7.222 3.027 7.222 7.214c0 2.573-1.06 4.742-2.879 6.003 5.404 1.463 8.282 5.953 8.282 13.016v2.623h-1.818v-2.522C25.807 19.238 21.967 15 15 15 8.082 15 4.193 19.288 4.193 26.906v2.523z"></path>
                                </svg>
                            </div>
                            <div class="HeaderButtons__text">MY Renault</div>
                        </a>
                    </div>
                </div>
            </div>
            <button class="MainHeader__overlay" tabindex="0" @click.prevent="expanded = false">
                <svg viewBox="0 0 30 30" class="MainHeader__close">
                    <path d="M29.999 2.512L27.5.012 14.999 12.504 2.498.012l-2.497 2.5L12.5 15.001.001 27.488l2.497 2.5 12.501-12.49L27.5 29.988l2.497-2.5-12.499-12.487z"></path>
                </svg>
                <span class="u-hidden-wording">close</span>
            </button>
        </div>
    </header>
</template>

<script>
    import axios from 'axios';
    import MainMenuEntry from "@/components/MainMenuEntry";

    export default {
        name: 'Header',

        components: {
            MainMenuEntry
        },

        data() {
            return {
                expanded: false,
                topNavigation: [],
                mainNavigation: []
            }
        },

        created() {
            if ("HEADER_SETTINGS" in window) {
                this.fetchNavigation(window.HEADER_SETTINGS);
            }
        },

        methods: {
            fetchNavigation({apiUri}) {
                axios.get(apiUri)
                    .then((response) => {
                        this.topNavigation = response.data.top_navigation;
                        this.mainNavigation = response.data.main_navigation;
                    })
            }
        }
    }
</script>

<style scoped>
    @import './assets/css/main.css';
    @import './assets/css/header.css';
    @import './assets/css/main_menu_range.css';
    @import './assets/css/main_megadropdown.css';

    @font-face {
        font-family: "readBeta2 sans-serif";
        font-weight: 400;
        font-display: swap;
        src: url(./assets/fonts/readBeta2-Light.woff2) format("woff2")
    }

    @font-face {
        font-family: "readBeta2 sans-serif";
        font-weight: 700;
        font-display: swap;
        src: url(./assets/fonts/readBeta2-Medium.woff2) format("woff2")
    }

    @font-face {
        font-family: "renaultLife, sans-serif";
        font-weight: 300;
        font-display: swap;
        src: url(./assets/fonts/RenaultLifeWeb-Light.woff) format("woff")
    }

    @font-face {
        font-family: "renaultLife, sans-serif";
        font-weight: 400;
        font-display: swap;
        src: url(./assets/fonts/RenaultLifeWeb-Regular.woff) format("woff")
    }

    @font-face {
        font-family: "renaultLife, sans-serif";
        font-weight: 700;
        font-display: swap;
        src: url(./assets/fonts/RenaultLifeWeb-Bold.woff) format("woff")
    }

    * {
        font-family: "readBeta2 sans-serif";
    }
</style>
