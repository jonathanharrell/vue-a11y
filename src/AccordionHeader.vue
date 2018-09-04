<script>
    export default {
        name: 'accordion-header',

        inject: ['accordionItemName', 'accordionItemState'],

        props: {
            level: {
                type: Number,
                required: false
            }
        },

        data () {
            return {
                headingAttrs: {
                    role: null,
                    'aria-level': null
                },
                buttonAttrs: {
                    role: null
                }
            }
        },

        mounted () {
            const heading = this.$el
            const headingTags = ['H1', 'H2', 'H3', 'H4', 'H5', 'H6']
            if (!headingTags.includes(heading.tagName)) {
                this.$set(this.headingAttrs, 'role', 'heading')

                if (!this.level) {
                    throw new TypeError('You must pass in a level value if you are not using a heading element.')
                }
                this.$set(this.headingAttrs, 'aria-level', this.level)
            } else {
                if (this.level) {
                    console.warn('You do not need to pass in a level value if you are using a heading element.')
                }
            }

            const childNodes = heading.childNodes
            if (childNodes.length > 1) {
                throw new TypeError('There should only be one element inside your heading element.')
            }

            const button = heading.childNodes[0]
            if (button.tagName !== 'BUTTON') {
                this.$set(this.buttonAttrs, 'role', 'button')
            }
        },

        render () {
            return this.$scopedSlots.default({
                headingAttrs: this.headingAttrs,
                buttonAttrs: {
                    ...this.buttonAttrs,
                    'aria-controls': `${this.accordionItemName}-panel`,
                    'aria-expanded': this.accordionItemState.expanded.toString(),
                },
                buttonEvents: {
                    click: () => {
                        this.accordionItemState.expanded = !this.accordionItemState.expanded
                    }
                }
            })
        }
    }
</script>
