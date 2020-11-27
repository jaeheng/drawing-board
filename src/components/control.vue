<template>
  <div class="control">
    <div class="item">
      <img src="../assets/pen.svg" alt="pen" class="pen size4" :class="{ active: size === 2 }" @click="setSize(2)">
      <img src="../assets/pen.svg" alt="pen" class="pen size3" :class="{ active: size === 4 }" @click="setSize(4)">
      <img src="../assets/pen.svg" alt="pen" class="pen size2" :class="{ active: size === 6 }" @click="setSize(6)">
      <img src="../assets/pen.svg" alt="pen" class="pen size1" :class="{ active: size === 8 }" @click="setSize(8)">
    </div>
    <div class="item">
      <div class="color" v-for="item in colorList" :key="item" :class="{ active: color === item }" @click="setColor(item)">
        <div class="circle" :style="{ background: item }"></div>
      </div>
    </div>
    <div class="item">
      <div class="btn">
        <button @click="$emit('clear')">清除</button>
      </div>
      <div class="btn">
        <button @click="$emit('download')">下载</button>
      </div>
    </div>
  </div>
</template>
<style lang="scss">
.control {
  position: fixed;
  left: 0;
  bottom: 0;
  height: 60px;
  width: 100%;
  background: #fff;
  display: flex;
  box-shadow: 0 -2px #5079bb, 0 -4px #ef3d0f5e;
  .item {
    flex: 1;
    display: flex;
    padding: 0 15px;
    border-right: 1px solid #eee;
    &:last-of-type {
      border-right: 0;
    }
    .active {
      background: #eee;
    }
  }
  .pen {
    display: inline-block;
    flex: 1;
    height: 30px;
    padding: 15px 0;
    &.size1 {
      height: 40px;
      padding: 10px 0;
    }
    &.size2 {
      height: 36px;
      padding: 12px 0;
    }
    &.size3 {
      height: 32px;
      padding: 14px 0;
    }
    &.size4 {
      height: 28px;
      padding: 16px 0;
    }
  }
  .color {
    flex: 1;
    padding-top: 18px;
    .circle {
      content: '';
      display: block;
      width: 24px;
      height: 24px;
      border-radius: 24px;
      margin: 0 auto;
      box-shadow: 0 0 1px;
    }
  }
  .btn {
    flex: 1;
    padding-top: 15px;
    button {
      border: none;
      outline: none;
      background: #4b7598;
      color: #fff;
      width: 80%;
      height: 30px;
      text-align: center;
      display: block;
      margin: 0 auto;
    }
  }
}
</style>

<script>
export default {
  data () {
    return {
      size: 2,
      color: '#000',
      colorList: ['#000', '#ffffff', '#ff2d51', '#0eb83a', '#4b5cc4']
    }
  },
  methods: {
    setSize (size) {
      this.size = size
      this.$emit('sizeChange', size)
    },
    setColor (color) {
      this.color = color
      this.$emit('colorChange', color)
    }
  }
}
</script>
