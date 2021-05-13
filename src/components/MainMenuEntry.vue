<template>
    <li :class="['MainMenuEntry', {'is-expanded': expanded}]">

        <button v-if="item.children" :class="['MainMenuEntry__link', {'is-opened': expanded}]" @click.prevent="toggle">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 185.343 185.343" class="SvgIcon MainMenuEntry__dropicon"><path d="M51.707 185.343a10.692 10.692 0 0 1-7.593-3.149 10.724 10.724 0 0 1 0-15.175l74.352-74.347L44.114 18.32c-4.194-4.194-4.194-10.987 0-15.175 4.194-4.194 10.987-4.194 15.18 0l81.934 81.934c4.194 4.194 4.194 10.987 0 15.175l-81.934 81.939a10.678 10.678 0 0 1-7.587 3.15z"></path></svg>
            {{ item.title }}
        </button>

        <a v-else :title="item.title" class="MainMenuEntry__link" :href="url">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 185.343 185.343" class="SvgIcon MainMenuEntry__dropicon">
                <path d="M51.707 185.343a10.692 10.692 0 0 1-7.593-3.149 10.724 10.724 0 0 1 0-15.175l74.352-74.347L44.114 18.32c-4.194-4.194-4.194-10.987 0-15.175 4.194-4.194 10.987-4.194 15.18 0l81.934 81.934c4.194 4.194 4.194 10.987 0 15.175l-81.934 81.939a10.678 10.678 0 0 1-7.587 3.15z"></path>
            </svg>
            {{ item.title }}
        </a>

        <div v-if="hasVehicleMenuChildren" class="EditorialContentZone MainMenuEntry__megaDropdown">
            <div class="MainMenuRangePicker MainMenuRangePicker_vertical">
                <template v-for="(vehicleMenu, vehicleMenuIndex) in vehicleMenuItems">
                    <button @click.prevent="setActiveVehicleMenu(vehicleMenuIndex)" :class="['MainMenuRangePicker__tab MainMenuRangePicker__tab_pos0', {'is-lastActive is-active': isVehicleMenuActive(vehicleMenuIndex)}]" :key="'btn-' + vehicleMenuIndex">
                        <p class="MainMenuRangePicker__tabTitle MainMenuMegaDropDownContent__tab">{{ vehicleMenu.title }}</p>
                    </button>
                    <div :class="['MainMenuRangePicker__content MainMenuRangePicker__content_pos0', {'is-lastActive is-active': isVehicleMenuActive(vehicleMenuIndex)}]" :id="'tab-' + vehicleMenuIndex" :key="'menu-' + vehicleMenuIndex">
                        <div class="MainMenuRangeModels">
                            <div class="MainMenuModel" v-for="(model, modelIndex) in vehicleMenu.children" :key="modelIndex">
                                <figure class="MainMenuModel__imageWrapper">
                                    <picture class="LazyPictureElement LazyPictureElement_loaded WebrenderPictureElement MainMenuModel__image is-ratio-forced">
                                        <source :srcset="model.icon + ' 2x'" media="(min-width: 1024px)">
                                        <source :srcset="model.icon + ' 2x'" media="(min-width: 641px)">
                                        <source :srcset="model.icon + ' 2x'">
                                        <img :src="model.icon" :alt="model.title" class="PictureElement__imgDefault">
                                        <noscript>
                                            <img :src="model.icon" :alt="model.title" />
                                        </noscript>
                                    </picture>
                                </figure>
                                <a :title="model.title" class="MainMenuModel__name" :href="model.url">{{ model.title }}</a>
                            </div>
                            <div class="MainMenuRangeModels__element">
                                <div class="MainMenuRangeModels__elementLinkInner">
                                    <button class="ButtonMore MainMenuRangeModels__link">
                                    <span class="ButtonMore__picto">
                                        <span class="u-hidden-wording">more</span>
                                    </span>
                                    </button>
                                    <a title="" class="MainMenuRangeModels__linkLabel" :href="vehicleMenu.url">Sva vozila</a>
                                </div>
                            </div>
                        </div>
                    </div>
                </template>

                <ul class="MainMenuRangePicker__links">
                    <li class="MainMenuRangePicker__listElement" v-for="(featuredLink, featuredLinkIndex) in featuredLinks" :key="featuredLinkIndex">
                        <a :title="featuredLink.title" class="MainMenuRangePicker__link MainMenuRangePicker__ctaLink" :href="featuredLink.url">
                            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 185.343 185.343" class="MainMenuRangePicker__svgArrowRight"><path d="M51.707 185.343a10.692 10.692 0 0 1-7.593-3.149 10.724 10.724 0 0 1 0-15.175l74.352-74.347L44.114 18.32c-4.194-4.194-4.194-10.987 0-15.175 4.194-4.194 10.987-4.194 15.18 0l81.934 81.934c4.194 4.194 4.194 10.987 0 15.175l-81.934 81.939a10.678 10.678 0 0 1-7.587 3.15z"></path></svg>
                            {{ featuredLink.title }}
                        </a>
                    </li>
                </ul>
            </div>
        </div>
        <div v-else class="EditorialContentZone MainMenuEntry__megaDropdown">
            <ul class="MainMenuMegaDropDownContent">
                <li class="MainMenuMegaDropDownContent__element" v-for="(child, childIndex) in children" :key="childIndex">
                    <div class="MainMenuMegaDropDownContent__linkColumn">
                        <div class="LinksColumn__toggle" role="button" tabindex="0">
                            <p class="LinksColumn__title">{{ child.title }}</p>
                            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 185.343 185.343" class="LinksColumn__svgArrowRight"><path d="M51.707 185.343a10.692 10.692 0 0 1-7.593-3.149 10.724 10.724 0 0 1 0-15.175l74.352-74.347L44.114 18.32c-4.194-4.194-4.194-10.987 0-15.175 4.194-4.194 10.987-4.194 15.18 0l81.934 81.934c4.194 4.194 4.194 10.987 0 15.175l-81.934 81.939a10.678 10.678 0 0 1-7.587 3.15z"></path></svg>
                        </div>
                        <ul class="LinksColumn__list" v-if="child.children">
                            <li class="LinksColumn__listElement" v-for="(child2, child2Index) in child.children" :key="child2Index">
                                <a
                                    :title="child2.title"
                                    class="LinksColumn__link"
                                    :href="child2.url">{{ child2.title }}</a>
                            </li>
                        </ul>
                        <ul class="LinksColumn__list" v-if="child.featured">
                            <li class="LinksColumn__listElement" v-for="(featured, featuredIndex) in child.featured" :key="featuredIndex">
                                <a
                                    :href="featured.url"
                                    :title="featured.title"
                                    class="LinksColumn__link LinksColumn__ctaLink"
                                    target="_blank"
                                    rel="noopener">
                                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 185.343 185.343" class="LinksColumn__linkSvgArrowRight"><path d="M51.707 185.343a10.692 10.692 0 0 1-7.593-3.149 10.724 10.724 0 0 1 0-15.175l74.352-74.347L44.114 18.32c-4.194-4.194-4.194-10.987 0-15.175 4.194-4.194 10.987-4.194 15.18 0l81.934 81.934c4.194 4.194 4.194 10.987 0 15.175l-81.934 81.939a10.678 10.678 0 0 1-7.587 3.15z"></path></svg>
                                    {{ featured.title }}
                                </a>
                            </li>
                        </ul>
                    </div>
                    <div class="MainMenuMegaDropDownContent__imageColumn">
                        <p class="ImageColumn__title"></p>
                    </div>
                </li>
            </ul>
        </div>
    </li>
</template>

<script>
    import {EventBus} from "@/utils";

    export default {
        name: "MainMenuEntry",

        props: {
            item: {
                type: Object
            }
        },

        data() {
            return {
                expanded: false,
                activeVehicleMenuIndex: 0
            }
        },

        created() {
            EventBus.$on('MainMenuEntryOpened', () => {
                this.expanded = false;
            });
        },

        computed: {
            url() {
                return this.item.children && this.item.children.length > 0 ? '#' : this.item.url;
            },

            hasVehicleMenuChildren() {
                if (!this.item.children) {
                    return false;
                }

                let vehicleMenu = this.item.children.find((c) => Number(c.vehicle_menu) === 1);

                return !!vehicleMenu;
            },

            children() {
                if (!this.item.children) {
                    return [];
                }

                let items = this.item.children;

                let columns = [];

                for (let i = 0; i < items.length; i++) {
                    let child = items [i];
                    if (child.children && child.children.length > 0) {
                        child.featured = [];
                        columns.push(child);
                    } else {
                        if (columns && columns.length > 0) {
                            columns [columns.length - 1].featured.push(child);
                        }
                    }
                }

                return columns;
            },

            vehicleMenuItems() {
                if (!this.item.children) {
                    return [];
                }

                return this.item.children.filter((c) => Number(c.vehicle_menu) === 1);
            },

            featuredLinks() {
                if (!this.item.children) {
                    return [];
                }

                return this.item.children.filter((c) => Number(c.vehicle_menu) === 0);
            }
        },

        methods: {
            toggle() {
                if (!this.expanded) {
                    EventBus.$emit('MainMenuEntryOpened', this);
                    this.expanded = true;
                } else {
                    this.expanded = false;
                }
            },

            isVehicleMenuActive(index) {
                return this.activeVehicleMenuIndex === index;
            },

            setActiveVehicleMenu(index) {
                this.activeVehicleMenuIndex = Number(index);
            }
        }
    }
</script>

<style scoped>

</style>