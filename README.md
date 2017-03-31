# 项目创建的可长久复用vue-components

1. checkbox

```
  <checkbox v-model="value"></checkbox>
```

2. navbar

```
// 父组件
<template>
<div>
  <navbar v-model="value" :data="data" @input="bindInput"></navbar>
<div>
</template>
<script>
export default {
  components: {
    'navbar': require('你的组件路径')
  },
  data() {
    value: 1,       // 通过value控制激活的选项
    data: [{
      value: 1,
      title: '选项1'  
    }, {
      value: 2,
      title: '选项2'
    }]
  },
  methods: {
    bindInput: funtion() {        // 监听组件的input或change事件
      // dosomething
    }
  }
}
</script>
```