<script setup lang="ts">
import { ref } from "vue";
import { invoke } from "@tauri-apps/api/tauri";
import { NButton } from "naive-ui";

const greetMsg = ref("");
const name = ref("");

async function greet() {
  // Learn more about Tauri commands at https://tauri.app/v1/guides/features/command
  greetMsg.value = await invoke("greet", { name: name.value });
}

// 测试箭头函数
const handleClick = () => {
  console.log("@131");
};
</script>

<template>
  <div class="card">
    <n-button @click="handleClick">naive-ui</n-button>
    <input id="greet-input" v-model="name" placeholder="Enter a name..." />
    <button type="button" @click="greet()">Greet</button>
    <div>my first mac app12323 我爱陈总</div>
  </div>

  <p>{{ greetMsg }}</p>
</template>
