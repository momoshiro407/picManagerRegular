<template>
  <form @submit.prevent="handleSubmit">
    <h2>ログイン</h2>
    <div class="form-group">
      <label for="email">メールアドレス</label>
      <input required type="text" id="email" v-model="email">
    </div>
    <div class="form-group">
      <label for="password">パスワード</label>
      <input required type="password" id="password" v-model="password">
    </div>
    <!-- <div v-if="error" class="error">{{ error }}</div> -->
    <button>ログイン</button>
  </form>
</template>

<script lang="ts">
import { defineComponent, ref } from "@vue/runtime-core"
import { useRouter } from 'vue-router'

export default defineComponent({
  setup() {
    const email = ref('')
    const password = ref('')
    const router = useRouter()

    const handleSubmit = async () => {
      router.push({ name: 'Home' })
    }

    return { email, password, handleSubmit }
  }
})
</script>

<style>
</style>