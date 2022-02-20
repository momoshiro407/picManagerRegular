<template>
  <!-- TODO: 暫定のテンプレートなので後でスタイルを調整する -->
  <h2>Upload pictures</h2>
  <form>
    <input type="file">
    <!-- <div v-if="fileError" class="error">{{ fileError }}</div> -->
    <!-- <div v-if="error" class="error">{{ error }}</div> -->
    <button>アップロード</button>
  </form>
</template>

<script lang="ts">
import { defineComponent } from "@vue/runtime-core"

export default defineComponent({
  name: 'AddPictures',
})
</script>

<style>

</style>