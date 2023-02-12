<script setup lang="ts">
import { ref } from "vue";
import { invoke } from "@tauri-apps/api/tauri";
import { NButton } from "naive-ui";
import { ask, confirm, message, open } from "@tauri-apps/api/dialog";
const greetMsg = ref("");
const name = ref("");

async function greet() {
  // Learn more about Tauri commands at https://tauri.app/v1/guides/features/command
  greetMsg.value = await invoke("greet", { name: name.value });
}

// 测试箭头函数
const handleClick = async () => {
  const selected = await open({
    multiple: true,
    filters: [
      {
        name: "Image",
        extensions: ["png", "jpeg"],
      },
    ],
  });
  if (Array.isArray(selected)) {
    // user selected multiple files
  } else if (selected === null) {
    // user cancelled the selection
  } else {
    // user selected a single file
  }
  // console.log(confirmed2);
};
</script>

<template>
  <div class="card">
    <n-button @click="handleClick">naive-ui</n-button>
    <input id="greet-input" v-model="name" placeholder="Enter a name..." />
    <button type="button" @click="greet()">Greet</button>
    <div>my first mac app</div>
  </div>

  <p>{{ greetMsg }}</p>
</template>
