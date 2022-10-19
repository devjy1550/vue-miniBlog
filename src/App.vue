<template>
  <div class="wrap">
    <BlogHeader />
    <BlogInput />
    <BlogList />
    <BlogFooter />
    <IntroView @closeintro="hideIntro" v-if="introShow" />
  </div>
</template>

<script>
import { ref } from "vue";
import BlogHeader from "@/components/BlogHeader.vue";
import BlogInput from "@/components/BlogInput.vue";
import BlogList from "@/components/BlogList.vue";
import BlogFooter from "@/components/BlogFooter.vue";
import IntroView from "@/components/IntroView.vue";
export default {
  components: {
    BlogHeader,
    BlogInput,
    BlogList,
    BlogFooter,
    IntroView,
  },
  setup() {
    // 첫화면(IntroView) 보여질 여부
    const introShow = ref(false);
    const hideIntro = () => {
      introShow.value = false;
    };

    return {
      hideIntro,
      introShow,
    };
  },
};
</script>

<style>
@charset 'utf-8';
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;700&display=swap");
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
ul,
li {
  list-style: none;
}
img {
  vertical-align: middle;
  border: 0;
}
a {
  color: #333;
  text-decoration: none;
}
html {
  font-size: 16px;
  overflow-x: hidden;
}
body {
  font-family: "Poppins", sans-serif;

  font-size: 14px;
  font-weight: 400;
  line-height: 1.2;
  letter-spacing: -0.64;
  color: #000;
  background-color: #f6f6f6;
}

.shadow {
  box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
}

.wrap {
  position: relative;
  display: block;
  width: calc(90% - 40px);
  padding: 80px;
  padding-top: 40px;
  background: #82e1fd;
  border-radius: 40px;
  margin: 0 auto;
  border: 20px double #0d4b5e;
  border-top: 0;
}

.wrap::before {
  content: "";
  position: absolute;
  display: block;
  top: 0;
  left: -20px;
  width: calc(100% + 40px);
  height: 140px;
  background-color: #f6f6f6;
}

.wrap::after {
  content: "";
  position: absolute;
  display: block;
  top: 100px;
  left: -20px;
  width: 100%;
  height: 40px;
  background: #82e1fd;
  z-index: 1;
  border-radius: 40px 40px 0 0;
  border: 20px double #0d4b5e;
  border-bottom: 0;
}
</style>
