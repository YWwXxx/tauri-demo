<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import { checkUpdate } from "@tauri-apps/api/updater";
import { onMounted, ref } from "vue";
import Greet from "./components/Greet.vue";
import Update from "./components/Update.vue";

const showUpdate = ref(false);
const created = async () => {
  try {
    const { shouldUpdate } = await checkUpdate();

    if (shouldUpdate) {
      // 检测到新版本，显示更新组件
      showUpdate.value = true;
    }
  } catch (error) {
    console.error(error);
  }
};

onMounted(() => {
  created();
});
</script>

<template>
  hello
  <Update key="11" v-if="showUpdate" />
</template>

<style scoped>
.logo.vite:hover {
  filter: drop-shadow(0 0 2em #747bff);
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #249b73);
}
</style>
