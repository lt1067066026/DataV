<template>
  <div class="dv-border-box-3" :ref="ref">
    <svg class="dv-border-svg-container" :width="width" :height="height">
      <polyline class="dv-bb3-line1"
        :points="`4, 4 ${width - 22} ,4 ${width - 22}, ${height - 22} 4, ${height - 22} 4, 4`" />
      <polyline class="dv-bb3-line2"
        :points="`10, 10 ${width - 16}, 10 ${width - 16}, ${height - 16} 10, ${height - 16} 10, 10`" />
      <polyline class="dv-bb3-line2"
        :points="`16, 16 ${width - 10}, 16 ${width - 10}, ${height - 10} 16, ${height - 10} 16, 16`" />
      <polyline class="dv-bb3-line2"
        :points="`22, 22 ${width - 4}, 22 ${width - 4}, ${height - 4} 22, ${height - 4} 22, 22`" />
    </svg>

    <div class="border-box-content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
import autoResize from '../../../mixin/autoResize'

export default {
  name: 'DvBorderBox3',
  mixins: [autoResize],
  data () {
    return {
      ref: 'border-box-3'
    }
  }
}
</script>