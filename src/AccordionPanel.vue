<script>
    export default {
        name: 'accordion-panel',

        inject: ['accordionItemName'],

        render () {
            return this.$scopedSlots.default({
                panelAttrs: {
                    id: `${this.accordionItemName}-panel`
                }
            })
        }
    }
</script>
