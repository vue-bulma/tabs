<template>
  <transition
    :name="animation"
    appear
    :appear-active-class="enterActiveClass"
    :enter-active-class="enterActiveClass"
    :leave-active-class="leaveActiveClass"
  >
    <div
      role="tabpanel"
      v-if="realSelected"
      :class="classObject"
      :aria-labelledby="label"
      :aria-hidden="hidden"
    >
      <slot></slot>
    </div>
  </transition>
</template>

<script>

const transitions = {
  fade: {
    enterClass: 'fadeIn',
    leaveClass: 'fadeOut'
  },
  'fade-horizontal-rtl': {
    enterClass: 'fadeInRight',
    leaveClass: 'fadeOutLeft'
  },
  'fade-horizontal-ltr': {
    enterClass: 'fadeInLeft',
    leaveClass: 'fadeOutRight'
  },
  'slide-horizontal-rtl': {
    enterClass: 'slideInRight',
    leaveClass: 'slideOutLeft'
  },
  'slide-horizontal-ltr': {
    enterClass: 'slideInLeft',
    leaveClass: 'slideOutRight'
  },
  'fade-vertical-dtu': {
    enterClass: 'fadeInUp',
    leaveClass: 'fadeOutUp'
  },
  'fade-vertical-utd': {
    enterClass: 'fadeInDown',
    leaveClass: 'fadeOutDown'
  },
  'slide-vertical-dtu': {
    enterClass: 'slideInUp',
    leaveClass: 'slideOutUp'
  },
  'slide-vertical-utd': {
    enterClass: 'slideInDown',
    leaveClass: 'slideOutDown'
  }
}

export default {

  props: {
    icon: String,
    selected: Boolean,
    disabled: Boolean,
    label: {
      type: String,
      required: true
    },
    mode: {
      type: String,
      default: 'out-in'
    }
  },

  data () {
    return {
      realSelected: this.selected,
      enterActiveClass: 'fadeIn',
      leaveActiveClass: 'fadeOut'
    }
  },

  beforeCreate () {
    this._isTabPane = true
  },

  mounted () {
    this.$parent.$on('select', this.select)
  },

  destroyed () {
    this.$parent.$off('select', this.select)
  },

  methods: {
    select (index, prevIndex) {
      const isCurr = this.index === index
      this.realSelected = isCurr
    }
  },

  computed: {
    classObject () {
      const { realSelected } = this
      return {
        'tab-pane': true,
        'animated': true,
        'is-active': realSelected,
        'is-deactive': !realSelected
      }
    },

    layout () {
      return this.$parent.layout
    },

    direction () {
      if (this.layout === 'top' || this.layout === 'bottom') {
        return 'horizontal'
      } else if (this.layout === 'left' || this.layout === 'right') {
        return 'vertical'
      }
      return ''
    },

    animation () {
      return this.$parent.animation
    },

    onlyFade () {
      return this.$parent.onlyFade
    },

    gte () {
      if (this.direction === 'vertical') {
        return 'utd'
      } else if (this.direction === 'horizontal') {
        return 'ltr'
      }
      return ''
    },

    lt () {
      if (this.direction === 'vertical') {
        return 'dtu'
      } else if (this.direction === 'horizontal') {
        return 'rtl'
      }
      return ''
    },

    index () {
      return this.$parent.tabPanes.indexOf(this)
    },

    hidden () {
      return this.realSelected ? 'false' : 'true'
    }
  }
}
  </script>
