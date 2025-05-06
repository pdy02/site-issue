<template>
  <div id="home">
    <p class="title">
      DY-永久发布页 - <span>pdy02.github.io</span>
    </p>

    <main>
      <ul v-if="isload">
        <li  v-for="item in data">
          <DyBtn @onClick="onClick" :data-site="item.site">{{ item.title }}</DyBtn>
        </li>
        <!-- <li>
          <DyBtn @onClick="onClick" data-site="https://note.dy-note.top/">笔记网站2</DyBtn>
        </li>
        <li>
          <DyBtn @onClick="onClick" data-site="https://note-1315129881.cos-website.ap-guangzhou.myqcloud.com/">
            旧vuePress笔记</DyBtn>
        </li>
        <li>
          <DyBtn @onClick="onClick" data-site="https://resource.dy-note.top/">捡漏资源网</DyBtn>
        </li> -->
      </ul>

      <div class="banner">
        <img src="https://note-1315129881.cos-website.ap-guangzhou.myqcloud.com/images/logo.jpg" />
      </div>
    </main>
  </div>
</template>

<script setup>
import { onMounted, reactive, ref } from 'vue';
import DyBtn from './components/UI/DyBtn.vue';

let data = reactive([]);
const isload = ref(false);
fetch('./data.json').then(val => val.json()).then(res => {
  data = res;
  if(data){
    isload.value = true;
  }
})
onMounted(() => {
})




const onClick = (el) => {
  const site = el.dataset.site;
  // console.log(el.dataset.site);
  open(site)
}
</script>

<style lang="scss" scoped>
#home {
  width: 700px;
  max-width: 90%;
  margin: 0 auto;
  padding: 24px;

  .title {
    height: 2rem;
    font-size: 2rem;
    font-weight: bold;
    text-align: left;
    line-height: 2rem;

    span {
      display: inline-block;
      line-height: 2rem;
      font-size: 1.5rem;
      font-weight: initial;
    }
  }
}

ul {
  padding: 4rem;
  list-style: none;

  li {
    display: flex;
    padding: 1rem;
    justify-content: center;
  }
}

.banner {
  display: flex;
  justify-content: center;

  img {
    width: 60%;
  }
}
</style>