<template>
  <div class="cytoscape"></div>
</template>
<style>
</style>
<script>
  import cytoscape from 'cytoscape';

export default {
    props: ['cyStyle', 'cyLayout'],
    data() {
        return {
            cy: null
        };
    },
    methods: {
        renderView: function(newElements) {
            // the only reliable way to do this is to recreate the view
            this.cy = cytoscape({
                container: document.getElementById(this.$el.id),
                elements: newElements,
                style: this.cyStyle,
                layout: this.cyLayout
            });
        }
    },
    mounted: function() {
        this.$emit('created', this);
    }
}
</script>
