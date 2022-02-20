<template>
  <div class="thumbnail-container">
    <div class="thumbnail" v-for="(url, index) in displayImages" :key="index">
      <img :src="url">
    </div>
  </div>
  <div>
    <Pagination
      :total="dummyImages.length"
      :imagesPerPage="imagesPerPage"
      :displayRange="displayRange"
      @currentPage="updateCurrentPage($event)"
    />
  </div>
</template>

<script lang="ts">
import { ref } from 'vue'
import { computed, defineComponent } from '@vue/runtime-core'
import Pagination from '@/components/Pagination.vue'

export default defineComponent({
  components: { Pagination },
  setup() {
    // 確認用ダミー画像データ
    const imageSet = [
      require('@/assets/images/green.jpg'),
      require('@/assets/images/red.jpg'),
      require('@/assets/images/blue.jpg'),
    ]
    // 三種類の画像をランダムに選んで配列に格納する
    const dummyImages = new Array(103).fill(null).map(() => imageSet[Math.floor(Math.random() * 3)])
    
    // ページネーション関係のパラメータ
    const currentPage = ref(1)
    const imagesPerPage = 10
    const displayRange = 9

    const updateCurrentPage = (page: number) => {
        currentPage.value = page
    }

    // 現在のページに表示する画像だけを抽出する
    const displayImages = computed(() => {
      const startIndex = (currentPage.value - 1) * imagesPerPage
      const endIndex = startIndex + imagesPerPage
      return dummyImages.slice(startIndex, endIndex)
    })
    
    return { dummyImages, currentPage, imagesPerPage, displayRange, updateCurrentPage, displayImages }
  }
})
</script>

<style scoped>
  .thumbnail-container {
    display: flex;
    flex-wrap: wrap;
  }
  .thumbnail {
    display: flex;
    margin-top: 20px;
    width: 200px;
    height: 200px;
    align-items: center;
    justify-content: center;
  }
  img {
    max-width: 195px;
    max-height: 195px;
  }
</style>
