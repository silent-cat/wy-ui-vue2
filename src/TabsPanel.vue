<template>
  <div class="tabs-panel-wrapper" :class="classes" v-if="active">
    <slot></slot>
  </div>
</template>

<script>
  export default {
    name: 'WYTabsPanel',
    inject: ['eventBus'],
    props: {
      name: {
        type: [String, Number],
        required: true
      }
    },
    data() {
      return {
        active: false
      }
    },
    computed: {
      classes() {
        return {
          active: this.active
        }
      }
    },
    created() {
      this.eventBus.$on('update:selected', (name) => {
        this.active = name === this.name
      })
    }
  }
</script>

<style lang="scss" scoped>
  .tabs-panel-wrapper {
    padding: 1em;

    &.active {
    }
  }
</style>