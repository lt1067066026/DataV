<template>
  <div class="dv-border-box-8" :ref="ref">
    <svg class="dv-svg-container" :width="width" :height="height">
      <defs>
        <path
          :id="path"
          :d="`M2.5, 2.5 L${width - 2.5}, 2.5 L${width - 2.5}, ${height - 2.5} L2.5, ${height - 2.5} L2.5, 2.5`"
          fill="transparent"
        />
        <radialGradient
          :id="gradient"
          cx="50%" cy="50%" r="50%"
        >
          <stop
            offset="0%" stop-color="#fff"
            stop-opacity="1"
          />
          <stop
            offset="100%" stop-color="#fff"
            stop-opacity="0"
          />
        </radialGradient>

        <mask :id="mask">
          <circle cx="0" cy="0" r="150" :fill="`url(#${gradient})`">
            <animateMotion
              dur="3s"
              :path="`M2.5, 2.5 L${width - 2.5}, 2.5 L${width - 2.5}, ${height - 2.5} L2.5, ${height - 2.5} L2.5, 2.5`"
              rotate="auto"
              repeatCount="indefinite"
            />
          </circle>
        </mask>
      </defs>

      <use
        stroke="#235fa7"
        stroke-width="1"
        :xlink:href="`#${path}`"
      />

      <use
        stroke="#4fd2dd"
        stroke-width="3"
        :xlink:href="`#${path}`"
        :mask="`url(#${mask})`"
      >
        <animate
          attributeName="stroke-dasharray"
          :from="`0, ${length}`"
          :to="`${length}, 0`"
          dur="3s"
          repeatCount="indefinite"
        />
      </use>
    </svg>

    <div class="border-box-content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
import autoResize from '../../../mixin/autoResize'

export default {
  name: 'DvBorderBox8',
  mixins: [autoResize],
  data () {
    const timestamp = Date.now()
    return {
      ref: 'border-box-8',
      path: `border-box-8-path-${timestamp}`,
      gradient: `border-box-8-gradient-${timestamp}`,
      mask: `border-box-8-mask-${timestamp}`
    }
  },
  computed: {
    length () {
      const { width, height } = this

      return (width + height - 5) * 2
    }
  }
}
</script>

<style lang="less">
.dv-border-box-8 {
  position: relative;
  width: 100%;
  height: 100%;

  svg {
    position: absolute;
    width: 100%;
    height: 100%;
    left: 0px;
    top: 0px;
  }

  .border-box-content {
    position: relative;
    width: 100%;
    height: 100%;
  }
}
</style>
