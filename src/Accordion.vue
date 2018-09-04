<script>
    export default {
        name: 'accordion',

        render (createElement) {
            return createElement('div', this.$slots.default)
        }
    }
</script>
