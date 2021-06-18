<template>
    <div class="plugin-helios-header-footer">         
        <div id="helios-footer" class="helios-footer helios-special-elements">
            <div class="page-footer">
                <footer>
                    <div class="module-container">
                        <div class="container-fluid">
                            <ul class="row footer-menu" data-fplugin="expand-content" data-fres="[&quot;xs&quot;]" data-fopts="{&quot;expandTriggerClass&quot;: &quot;open&quot;, &quot;collapsedDisplay&quot; : &quot;&quot;, &quot;grouped&quot; : &quot;true&quot;, &quot;collapsedDisplay&quot; : &quot;&quot;}">
                                <li v-for="(item, itemIndex) in mainNavigation" :key="itemIndex" class="col-xs-12 col-sm-4 col-md-3 expand-box" @click.prevent="toggle(itemIndex)">
                                    <div :class="['menu-group-name','trigger', {'open': isVisible(itemIndex)}]">{{ item.title }}</div>
                                    
                                    <ul :class="['footer-menu', 'container-show', {'displayBlock' :  isVisible(itemIndex)}]">

                                        <li v-for="(child, childIndex) in item.children" :key="childIndex">
                                            <a :title="child.title" :href="child.url"><span>{{ child.title }}</span></a>
                                        </li>
                                        
                                    </ul>
                                </li>
                                
                                <li class="col-xs-12 col-sm-12 col-md-3 social-menu">
                                    <div class="menu-group-name">Renault na društvenim mrežama</div>
                                    <div class="social-links">
                                        
                                        <a href="https://www.facebook.com/RenaultCrnaGora/" data-phf-ico-before="" title="Posjetite nas na Facebook-u" target="_blank" class="ico-before" rel="nofollow"></a>
                                        
                                        <a href="https://www.instagram.com/renault.me/" data-phf-ico-before="" title="Posjetite nas na Instagram-u" target="_self" class="ico-before" rel="nofollow"></a>
                                        
                                        <a href="https://twitter.com/groupe_renault " data-phf-ico-before="" title="Posjetite nas na Twitter-u (engleski)" target="_blank" class="ico-before" rel="nofollow"></a>
                                        
                                        <a href="https://www.youtube.com/user/renault" data-phf-ico-before="" title="Posjetite nas na You Tube-u (engleski)" target="_blank" class="ico-before" rel="nofollow"></a>
                                        
                                    </div>
                                </li>
                                
                            </ul>
                        </div>
                    </div>
                    
                    <div class="bottom-menu">
                        <div class="module-container row">
                            <ul class="footer-links footer-options col-xs-12 col-md-6 ">

                                <li
                                    v-for="(legalItem, legalItemIndex) in legalNavigation"
                                    :key="legalItemIndex">

                                    <a
                                        :title="legalItem.title"
                                        :href="legalItem.url">
                                        <span>
                                            {{ legalItem.title }}
                                        </span>
                                    </a>
                                </li>
                                
                            </ul>
                            <ul class="footer-links footer-legal col-xs-12 col-md-6 ">
                                
                                <li
                                    v-for="(legalItem, legalItemIndex) in legalNavigation"
                                    :key="legalItemIndex">

                                    <a
                                        :title="legalItem.title"
                                        :href="legalItem.url">
                                        <span>
                                            {{ legalItem.title }}
                                        </span>
                                    </a>
                                </li>
                                
                                <li class="footer-legal_item"><span class="copyright" title=" © Renault 2021"> © Renault 2021</span></li>
                            </ul>
                        </div>
                    </div>
                    
                </footer>
            </div>
        </div>
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
    @import './assets/css/main.css';

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
    @font-face{
        font-family:NouvelR-Regular;
        font-weight:400;
        font-display:swap;
        src:url(./assets/fonts/NouvelR-Regular.woff2) format("woff2")
    }
    @font-face{
        font-family:NouvelR-Bold;
        font-weight:700;
        font-display:swap;
        src:url(./assets/fonts/NouvelR-Bold.woff2) format("woff2")
    }
    @font-face{
        font-family:Pictos;
        font-style: normal;
        font-weight: 400;
        src:url(./assets/fonts/PictosComplete-Regular.woff) format("woff")
    }
    * {
        font-family: NouvelR-Regular,sans-serif,Arial;
    }
    .displayBlock {
        display: block !important;
    }
</style>