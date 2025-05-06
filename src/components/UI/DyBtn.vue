<template>
  <div class="dy-btn" @click="onClick" ref="tg">
    <button> <slot></slot> </button>
  </div>
</template>

<script setup>
import { ref } from 'vue';
// 监听组件外部的自定义事件
const emit = defineEmits(['onClick'])
// btn组件的div跟元素
const tg = ref();

const onClick = () => {
  emit('onClick', tg.value)
}
</script>

<style lang="scss" scoped>
.dy-btn{
  display: block;
  width: fit-content;
  display: flex;
  align-items: center;
  background-color: #3498db;
  border-radius: 1.2rem;
  padding: 0.3rem 1rem;
  cursor: pointer;
  transition: all 0.3s;
  &:hover{
    background-color: #3498dbaa;
    // filter: grayscale(0.5);
  }
}
button{
  cursor: inherit;
  color: #fff;
  border: none;
  background: transparent;
}
</style>