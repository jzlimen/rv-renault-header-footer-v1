<template>
    <div class="ContentZone ContentZone__footer">
        <div class="Prefooter">
            <div class="Prefooter__buttonContainer">
                <button class="Prefooter__returnToTop" type="button" @click.prevent="scrollToTop">
                    <div class="Button__content">Vratite se na vrh stranice</div>
                </button>
            </div>
            <ul class="Prefooter__content Slice Slice_childrenMobileWrap">
                <li class="SubPrefooter Slice__element">
                    <span class="SubPrefooter__link">
                       <picture class="LazyPictureElement LazyPictureElement_loaded SubPrefooter__icon is-contained">
                          <img src="https://cdn.group.renault.com/pictograms/D2-0_Pre-footer/renault-location.svg.asset.svg/1525420466579.svg" alt="SubPrefooter Icon" class="PictureElement__imgDefault">
                          <noscript><img src="https://cdn.group.renault.com/pictograms/D2-0_Pre-footer/renault-location.svg.asset.svg/1525420466579.svg" alt="SubPrefooter Icon" /></noscript>
                       </picture>
                       <p class="SubPrefooter__text"><span class="SubPrefooter__mainText">Ovlaštena mreža nadohvat ruke</span><span class="SubPrefooter__SecondaryText">Više od 20 prodajno-servisnih lokacija</span></p>
                    </span>
                </li>
                <li class="SubPrefooter Slice__element">
                    <span class="SubPrefooter__link">
                       <picture class="LazyPictureElement LazyPictureElement_loaded SubPrefooter__icon is-contained">
                          <img src="https://cdn.group.renault.com/pictograms/D2-0_Pre-footer/renault-client-service.svg.asset.svg/1525420487650.svg" alt="SubPrefooter Icon" class="PictureElement__imgDefault">
                          <noscript><img src="https://cdn.group.renault.com/pictograms/D2-0_Pre-footer/renault-client-service.svg.asset.svg/1525420487650.svg" alt="SubPrefooter Icon" /></noscript>
                       </picture>
                       <p class="SubPrefooter__text"><span class="SubPrefooter__mainText">Pomoć na cesti 24h</span><span class="SubPrefooter__SecondaryText">U Hrvatskoj i Europi</span></p>
                    </span>
                </li>
                <li class="SubPrefooter Slice__element">
                    <span class="SubPrefooter__link">
                       <picture class="LazyPictureElement LazyPictureElement_loaded SubPrefooter__icon is-contained">
                          <img src="https://cdn.group.renault.com/pictograms/D2-0_Pre-footer/renault-warranty.svg.asset.svg/1525420436718.svg" alt="SubPrefooter Icon" class="PictureElement__imgDefault">
                          <noscript><img src="https://cdn.group.renault.com/pictograms/D2-0_Pre-footer/renault-warranty.svg.asset.svg/1525420436718.svg" alt="SubPrefooter Icon" /></noscript>
                       </picture>
                       <p class="SubPrefooter__text"><span class="SubPrefooter__mainText">Vozite s povjerenjem</span><span class="SubPrefooter__SecondaryText">zahvaljujući jamstvima tvrtke Renault</span></p>
                    </span>
                </li>
                <li class="SubPrefooter Slice__element">
                    <span class="SubPrefooter__link">
                       <picture class="LazyPictureElement LazyPictureElement_loaded SubPrefooter__icon is-contained">
                          <img src="https://cdn.group.renault.com/pictograms/D2-0_Pre-footer/renault-trade-in.svg.asset.svg/1525420415798.svg" alt="SubPrefooter Icon" class="PictureElement__imgDefault">
                          <noscript><img src="https://cdn.group.renault.com/pictograms/D2-0_Pre-footer/renault-trade-in.svg.asset.svg/1525420415798.svg" alt="SubPrefooter Icon" /></noscript>
                       </picture>
                       <p class="SubPrefooter__text"><span class="SubPrefooter__mainText">Olakšajte si svakodnevni život</span><span class="SubPrefooter__SecondaryText">uz MY Renault</span></p>
                    </span>
                </li>
            </ul>
        </div>
        <footer class="Footer">
            <div class="Footer__preFooter">
                <div class="Footer__preFooterColumns">
                    <div v-for="(item, itemIndex) in mainNavigation" :key="itemIndex" class="FooterColumn Footer__preFooterColumn" role="button" tabindex="0">
                        <p class="FooterColumn__titleColumn" @click.prevent="toggle(itemIndex)">
                            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 30 30" class="FooterColumn__SvgIcon">
                                <path d="M1.822 7.527a1.058 1.058 0 0 0-1.46 1.532l14.384 13.707L29.624 9.071a1.059 1.059 0 0 0-1.432-1.558l-13.42 12.354-12.95-12.34z"></path>
                            </svg>
                            {{ item.title }}
                        </p>
                        <ul :class="['FooterColumn__linksList', {'is-visible': isVisible(itemIndex)}]">
                            <li class="FooterColumn__linkContainer" v-for="(child, childIndex) in item.children" :key="childIndex">
                                <a :title="child.title" class="FooterColumn__link" :href="child.url">{{ child.title }}</a>
                            </li>
                        </ul>
                    </div>
                </div>
                <div class="FooterSocialNetwork Footer__preFooterSocial">
                    <p class="FooterSocialNetwork__titleColumn"> Ostanite povezani</p>
                    <ul class="FooterSocialNetwork__socialNetworkLinks">
                        <li v-for="(socialItem, socialItemIndex) in socialNavigation" :key="socialItemIndex" class="FooterSocialNetwork__socialNetworkElement">
                            <a :href="socialItem.url" :title="socialItem.title" class="FooterSocialNetwork__socialNetworkLink" target="_blank" rel="noopener">
                                <picture class="LazyPictureElement LazyPictureElement_loaded FooterSocialNetwork__socialNetworkIcon">
                                    <img :src="socialItem.icon" alt="social-logo" class="PictureElement__imgDefault">
                                    <noscript>
                                        <img :src="socialItem.icon" alt="social-logo" />
                                    </noscript>
                                </picture>
                            </a>
                        </li>
                    </ul>
                </div>
            </div>
            <nav class="FooterLegal">
                <ul class="FooterLegal__list">
                    <li
                        v-for="(legalItem, legalItemIndex) in legalNavigation"
                        :key="legalItemIndex"
                        class="FooterLegal__element">

                        <a
                            :title="legalItem.title"
                            class="FooterLegal__link"
                            :href="legalItem.url">
                            {{ legalItem.title }}
                        </a>
                    </li>
                </ul>
                <span class="FooterLegal__copyright">© <!-- -->renault<!-- --> <!-- -->2017 - 2021</span>
            </nav>
        </footer>
    </div>
</template>

<script>
    import axios from "axios";

    export default {
        name: "Footer",

        created() {
            if ("FOOTER_SETTINGS" in window) {
                this.fetchNavigation(window.FOOTER_SETTINGS);
            }
        },

        data() {
            return {
                visibleIndex: null,
                mainNavigation: [],
                socialNavigation: [],
                legalNavigation: []
            }
        },

        methods: {
            fetchNavigation({apiUri}) {
                axios.get(apiUri)
                    .then((response) => {
                        this.mainNavigation = response.data.main_navigation;
                        this.socialNavigation = response.data.social_navigation;
                        this.legalNavigation = response.data.legal_navigation;
                    })
            },

            isVisible(itemIndex) {
                return this.visibleIndex === itemIndex;
            },

            toggle(itemIndex) {
                if (this.visibleIndex === itemIndex) {
                    this.visibleIndex = null;
                } else {
                    this.visibleIndex = Number(itemIndex);
                }
            },

            scrollToTop() {
                window.scrollTo({ top: 0, behavior: 'smooth' });
            }
        }
    }
</script>

<style scoped>
    @import './assets/css/pre_footer.css';
    @import './assets/css/footer.css';

    @font-face{
        font-family:"readBeta2 sans-serif";
        font-weight:400;
        font-display:swap;
        src:url(./assets/fonts/readBeta2-Light.woff2) format("woff2")
    }
    @font-face{
        font-family:"readBeta2 sans-serif";
        font-weight:700;
        font-display:swap;
        src:url(./assets/fonts/readBeta2-Medium.woff2) format("woff2")
    }
    @font-face{
        font-family:"RenaultLife";
        font-weight:300;
        font-display:swap;
        src:url(./assets/fonts/RenaultLifeWeb-Light.woff) format("woff")
    }
    @font-face{
        font-family:"RenaultLife";
        font-weight:400;
        font-display:swap;
        src:url(./assets/fonts/RenaultLifeWeb-Regular.woff) format("woff")
    }
    @font-face{
        font-family:"RenaultLife";
        font-weight:700;
        font-display:swap;
        src:url(./assets/fonts/RenaultLifeWeb-Bold.woff) format("woff")
    }
    * {
        font-family: "readBeta2 sans-serif";
    }
</style>