
<script setup>
  import api from './config';
  import { onMounted, ref } from 'vue';
  const response = ref([])

  onMounted(()=> {
    api.get("/posts").then(res => {
      response.value = res.data.posts
    })
  })
</script>
<template>
  <main>
  <div v-for="datas in response" class="container">
    <div class="subcont">
      <div class="title">
        {{ datas.title }}
      </div>
      <div class="body">
        {{ datas.body }}
      </div>
      <div v-for="tg in datas.tags">
        <div class="tag">{{ tg }}</div>
      </div>
      <div v-for="react in datas.reactions">
      <div>{{ react }}</div>
      </div>
      <div class="views">{{ datas.views }} views</div>
    </div>
  </div>
  </main>
</template>
<style scoped>
  

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

main {
  min-height: 100vh;
  background-color: #f4f4f2;
  padding: 48px 24px;
  font-family: 'DM Sans', sans-serif;
}

.container {
  max-width: 680px;
  margin: 0 auto 24px auto;
}


.subcont {
  background: #ffffff;
  border-radius: 16px;
  padding: 32px 36px;
  box-shadow:
    0 1px 2px rgba(0, 0, 0, 0.04),
    0 4px 12px rgba(0, 0, 0, 0.06),
    0 12px 32px rgba(0, 0, 0, 0.04);
  border: 1px solid rgba(0, 0, 0, 0.05);
}

.title {
  font-family: 'DM Serif Display', serif;
  font-size: 1.4rem;
  color: #1a1a1a;
  line-height: 1.35;
  margin-bottom: 14px;
  letter-spacing: -0.01em;
}

.body {
  font-size: 0.925rem;
  font-weight: 300;
  color: #555;
  line-height: 1.75;
  margin-bottom: 22px;
  border-left: 3px solid #e8e8e6;
  padding-left: 14px;
}

.subcont > div:has(> .tag) {
  display: inline;
}

.tag {
  display: inline-block;
  font-size: 0.75rem;
  font-weight: 500;
  letter-spacing: 0.06em;
  text-transform: uppercase;
  color: #777;
  background: #f0f0ee;
  border: 1px solid #e4e4e3;
  border-radius: 6px;
  padding: 4px 10px;
  margin: 0 6px 8px 0;
}

.views {
  font-size: 0.78rem;
  font-weight: 400;
  color: #aaa;
  letter-spacing: 0.03em;
  padding-top: 16px;
  border-top: 1px solid #f0f0ee;
  margin-top: 16px;
  text-align: right;
}
</style>
