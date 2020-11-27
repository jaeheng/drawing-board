<template>
  <div class="pad" id="pad">
    <vue-signature
        ref="s1"
        :stroke-size="size"
        :stroke-color="color"
        :width="width"
        :height="height" />
    <control
        @sizeChange="sizeChange"
        @colorChange="colorChange"
        @clear="clear"
        @download="download"
    />
  </div>
</template>

<script>
import VueSignature from 'vue-signature-simple'
import control from './control'
export default {
  name: 'pad',
  components: {
    VueSignature,
    control
  },
  data () {
    return {
      width: 0,
      height: 0,
      size: 2,
      color: '#000'
    }
  },
  methods: {
    init () {
      this.width = document.getElementById('pad').clientWidth
      this.height = document.getElementById('pad').clientHeight
    },
    sizeChange (size) {
      this.size = size
    },
    colorChange (color) {
      this.color = color
    },
    clear () {
      this.$refs.s1.clear()
    },
    download () {
      const base64Data = this.$refs.s1.getSignature()
      const filename = new Date().toLocaleDateString()
      const aTag = document.createElement('a')
      aTag.href = base64Data
      aTag.download = filename
      document.body.appendChild(aTag)
      aTag.click()
      document.body.removeChild(aTag)
    }
  },
  mounted() {
    this.$nextTick(() => {
      this.init()
    })
  }
}
</script>
