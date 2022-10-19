<template>
  <header class="header">
    <div class="logo">
      <h1>{{ title }}</h1>
      <img :src="require('@/assets/images/title-logo.png')" />
      <span>-Check List-</span>
    </div>
  </header>
</template>

<script>
import { ref } from "vue";
import { useStore } from "vuex";
export default {
  setup() {
    const title = ref("");
    const store = useStore();
    title.value = store.state.headerText;
    return {
      title,
    };
  },
};
</script>

<style>
/* h1 {
  text-align: center;
  font-weight: 500;
} */
.header {
  position: relative;
  display: block;
  z-index: 2;
}
.logo {
  position: relative;
  display: block;
  width: 36%;
  height: 160px;
  background-color: #7a8fa4;
  border-radius: 35px;
  margin: 0 auto;
  padding: 10px;
  border: 10px double rgb(39, 35, 35);
  text-align: center;
}
.logo img {
  width: 80px;
  height: 80px;
  position: relative;
  display: block;
  margin: 0 auto;
  z-index: 3;
}

.logo span {
  position: relative;
  font-size: 32px;
  line-height: 40px;
  font-weight: 700;
  display: inline-block;
  color: #f0f0f0;
}
</style>
