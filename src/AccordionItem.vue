<script>
    export default {
        name: 'accordion-item',

        props: {
            name: {
                type: String,
                required: true
            }
        },

        data () {
            return {
                sharedState: {
                    expanded: false
                }
            }
        },

        provide () {
            return {
                accordionItemName: this.name,
                accordionItemState: this.sharedState
            }
        },

        render () {
            return this.$scopedSlots.default({
                expanded: this.sharedState.expanded
            })
        }
    }
</script>
