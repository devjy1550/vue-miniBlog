<template>
  <div class="clear-all-wrap">
    <span class="clear-all-bt" @click="clearAllMemo">Clear</span>
    <span class="copy">© 2022. KIM JEONG YONG All rights reserved.</span>
  </div>
</template>

<script>
import { useStore } from "vuex";
export default {
  setup() {
    const store = useStore();

    const clearAllMemo = () => {
      // context.emit('deleteitem')
      // store.commit('CLEAR_MEMO');
      store.dispatch("fetchClearMemo");
    };

    return {
      clearAllMemo,
    };
  },
};
</script>

<style>
.clear-all-wrap {
  position: relative;
  display: block;
  width: 100%;

  line-height: 50px;
  background-color: rgb(255, 253, 234);

  text-align: center;
  margin: 0 auto;
  margin-top: 20px;
  border-radius: 5px;
}
.clear-all-bt {
  display: inline-block;
  width: 80%;
  height: 50px;
  cursor: pointer;
  border: 2px solid rgb(255, 225, 93);
  border-radius: 5px;
  margin-top: 10px;
}

.clear-all-bt:hover {
  border: 2px solid rgb(238, 207, 68);
  background-color: rgb(253, 247, 194);
  font-weight: 500;
}

.copy {
  display: block;
  font-size: 12px;
  font-weight: 500;
  line-height: 30px;
  white-space: nowrap;
}
</style>
