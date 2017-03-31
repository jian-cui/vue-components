<template>
<ul class="nav" @click="bindClick">
  <li :data-value="item.value" v-for="item in data" :class="{ 'nav-active': isActive == item.value }">
    <span>{{ item.title }}</span>
  </li>
</ul>
</template>

<script>
export default {
  props: ['value', 'data'],
  data() {
    return {
      isActive: ''
    }
  },
  methods: {
    bindClick: function (ev) {
      let target = ev.target || ev.srcElement
      while(target) {
        if (target.tagName.toLowerCase() === 'li') {
          this.isActive = target.dataset.value
          this.$emit('input', target.dataset.value)
          this.$emit('change', target.dataset.value)
          break
        }
        target = target.parentNode
      }
    }
  },
  created: function () {
    this.isActive = this.value
  }
}
</script>

<style lang='less'>
@import '../../common/conf.less';

ul.nav {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100rem/@r;
  box-sizing: content-box;
  border-bottom: 1px solid @border;
  background-color: #fff;
  color: #555;
  margin-bottom: 10rem/@r;
  li {
    flex: 1;
    text-align: center;
    font-size: 0;
    display: block;
    span {
      display: inline-block;
      height: 100rem/@r;
      line-height: 100rem/@r;
      font-size: 28rem/@r;
      // box-sizing: content-box;
      border-bottom-style: solid;
      border-bottom-width: 2px;
      border-bottom-color: transparent;
    }
    &.nav-active span{
      border-bottom-color: @red-light;
    }
  }
}
</style>