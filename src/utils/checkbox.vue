<template>
  <label class="common-checkbox" :class="{ 'is-checked': isChecked }">
    <input type="checkbox" @change="handleChange" :checked="value" ref="input">
    <span class="common-checkbox-fake"></span>
    <div class="common-checkbox-text">
      <slot></slot>
    </div>
  </label>
</template>

<script>
export default {
  name: 'checkbox',
  props: {
    // checked: Boolean,
    value: Boolean
  },
  data() {
    return {
      isChecked: false
    }
  },
  methods: {
    handleChange: function (ev) {
      // console.log('inner data', this.value)
      let checked = ev.target.checked
      // console.log('before emit input', this.value)
      this.isChecked = checked
      this.$emit('input', checked)
    }
  },
  created: function () {
    this.isChecked = this.valueß
  }
}
</script>

<style lang="less">
@import '../less/conf.less';

.common-checkbox {
  input {
    display: none;
  }
  .common-checkbox-fake {
    float: left;
    box-sizing: border-box;
    width: 36rem/@r;
    height: 36rem/@r;
    border-radius: 50%;
    border: 1px solid @red-light;
    background-color: #fff;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  &.is-checked>.common-checkbox-fake:after {
    content: '';
    width: 16rem/@r;
    height: 16rem/@r;
    background-color: @red-light;
    border-radius: 50%;
  }
  .common-checkbox-text {
    margin-left: 46rem/@r;
    line-height: 36rem/@r;
    color: inherit;
  }
}
</style>