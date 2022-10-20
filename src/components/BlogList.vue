<template>
  <div class="list-wrap">
    <TransitionGroup name="list" tag="ul">
      <!-- <ul> -->
      <li v-for="(item, index) in items" v-bind:key="index" class="shadow">
        <i
          class="fas fa-check-circle check-bt"
          @click="updateMemo(item, index)"
          :class="{ memoComplete: item.complete }"
        ></i>

        <span :class="{ memoCompleteTxt: item.complete }">
          {{ item.memotitle }}
        </span>

        <div class="info">
          <span
            class="icon"
            :style="{
              backgroundImage:
                'url(' + require(`@/assets/images/${item.memoicon}`) + ')',
            }"
          ></span>
          <span class="date">{{ item.memodate }}</span>
          <span class="remove-bt" @click="removeMemo(item.id, index)">
            <i class="fas fa-trash"></i>
          </span>
        </div>
      </li>
      <!-- </ul> -->
    </TransitionGroup>
  </div>
</template>

<script>
import { useStore } from "vuex";
import { computed } from "vue";

export default {
  setup() {
    // vuex store 사용
    const store = useStore();

    store.dispatch("fetchReadMemo");

    const items = computed(() => store.getters.getMemoArr);

    const removeMemo = (id, index) => {
      // context.emit('removeitem', item, index);
      // store.commit('DELETE_MEMO', {item, index})
      store.dispatch("fetchDeleteMemo", { id, index });
    };

    const updateMemo = (item, index) => {
      // context.emit("updateitem", item, index);
      // store.commit('UPDATE_MEMO', {item, index})
      store.dispatch("fetchUpdateMemo", { item, index });
    };

    return {
      removeMemo,
      updateMemo,
      items,
    };
  },
};
</script>

<style scoped>
li {
  display: flex;
  min-height: 50px;
  line-height: 50px;
  margin-top: 20px;
  background-color: rgb(255, 253, 234);

  border-radius: 5px;
  padding-left: 20px;
}

.info {
  margin-left: auto;
  height: 50px;
}

.icon {
  display: inline-block;
  width: 50px;
  height: 50px;
  background-size: 30px 15px;
  background-repeat: no-repeat;
  background-position: center;
}
.date {
  position: relative;
  display: inline-block;
  width: 160px;
  vertical-align: top;
  color: rgb(0, 0, 0);
  margin-left: 10px;
  cursor: pointer;
  text-align: center;
  line-height: 30px;
  font-size: 16px;
  padding: 10px 0;
  /* background: rgb(119, 142, 175); */
}
.remove-bt {
  position: relative;
  display: inline-block;
  vertical-align: top;
  width: 50px;
  color: rgb(255, 188, 44);
  cursor: pointer;
  text-align: center;
  font-size: 16px;
}

.remove-bt:hover {
  color: rgb(224, 161, 24);
}

.check-bt {
  color: rgb(255, 188, 44);
  line-height: 50px;
  margin-right: 10px;
  cursor: pointer;
}

.memoComplete {
  color: #b3adad;
}

.memoCompleteTxt {
  color: #b3adad;
  text-decoration: line-through;
}
/* 애니메이션 */
.list-enter-active,
.list-leave-active {
  transition: all 0.5s ease;
}
.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateX(30px);
}
</style>
