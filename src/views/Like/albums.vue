<template>
  <div class="like-albums">
    <Transition name="fade" mode="out-in">
      <div v-if="userLikeData.albums?.length" class="list">
        <!-- 列表 -->
        <MainCover :data="likeAlbumsData" type="album" />
      </div>
      <n-empty
        v-else
        description="当前暂无收藏专辑"
        class="tip"
        style="margin-top: 60px"
        size="large"
      />
    </Transition>
  </div>
</template>

<script setup>
import { storeToRefs } from "pinia";
import { siteData } from "@/stores";
import formatData from "@/utils/formatData";

const data = siteData();
const { userLikeData } = storeToRefs(data);

// 处理专辑数据
const likeAlbumsData = computed(() => {
  return formatData(userLikeData.value.albums, "album");
});
</script>
