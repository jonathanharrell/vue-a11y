<template>
    <div id="app">
        <h2>Accordion</h2>
        <accordion>
            <accordion-item name="item-1">
                <div slot-scope="{ expanded }">
                    <accordion-header>
                        <h2 slot-scope="{ headingAttrs, buttonAttrs, buttonEvents }" v-bind="headingAttrs">
                            <button v-bind="buttonAttrs" v-on="buttonEvents">
                                item 1: {{ expanded }}
                            </button>
                        </h2>
                    </accordion-header>
                    <accordion-panel>
                        <div slot-scope="{ panelAttrs }" v-bind="panelAttrs" v-show="expanded">
                            panel
                        </div>
                    </accordion-panel>
                </div>
            </accordion-item>
        </accordion>
    </div>
</template>

<script>
    import Accordion from './Accordion'
    import AccordionItem from './AccordionItem'
    import AccordionHeader from './AccordionHeader'
    import AccordionPanel from './AccordionPanel'

    export default {
        name: 'app',

        components: {
            Accordion,
            AccordionItem,
            AccordionHeader,
            AccordionPanel
        }
    }
</script>
