<script setup>
definePageMeta({
  layout: 'custom',
})
const searchKeyword = ref('')
const router = useRouter()

const search = (keyword) => {
  router.push({path:'/search',query:{keyword:encodeURIComponent(keyword)}})
}
const donate = () => {
  router.push({path:'/donate'})
}
const hotKeywords = ref(['庆余年2','歌手2024','庆余年','我的阿勒泰','新生'])
</script>

<template>
  <div class="bg-[#ffffff] min-h-screen py-[60px]">

    <div class="flex flex-row items-center justify-center gap-3 mt-[80px]">
      <img class="w-[40px] h-[40px] sm:w-[60px] sm:h-[60px]" src="@/assets/my-logo.png" alt="logo">
      <h1 class="text-[18px] sm:text-[24px] font-serif font-bold ">爱盼-网盘资源搜索</h1>
    </div>

    <div class="max-w-[1240px] mx-auto mt-[20px]">
      <div class="w-[80%] md:w-[700px] mx-auto border border-slate-300 font-mono overflow-hidden rounded-[50px]">
        <client-only>
          <el-input class="h-[40px] sm:h-[50px]"
                    v-model="searchKeyword"
                    placeholder="请输入关键词搜索"
                    @keydown.enter="search(searchKeyword)"
                    prefix-icon="Search"
          >
          </el-input>
        </client-only>
      </div>
    </div>

    <div class="max-w-[1240px] mx-auto mt-[20px]">
      <div class="flex flex-row flex-wrap gap-1 justify-center">
        <el-tag class="mx-1 cursor-pointer"
                v-for="keyword in hotKeywords"
                :key="keyword"
                type="info"
                @click="search(keyword)"
        >
          {{ keyword }}
        </el-tag>
      </div>

    </div>

    <div class="fixed bottom-0 left-0 right-0 bg-white p-3">
      <div class="flex flex-row items-center justify-center  gap-3 my-3">
        <a class="" href="https://github.com/unilei/aipan-netdisk-search">
          <img class="w-[50px] h-[50px]" src="@/assets/github.png" alt="github">
        </a>
        <el-button color="#ffffff" @click="donate()">
          <img  class="w-[50px] h-[50px]" src="@/assets/donation/dashang.svg" alt="打赏">
        </el-button>
      </div>
      <p class="text-center text-[8px] sm:text-[12px] text-slate-400">
        声明：本站不产生/存储任何数据，也从未参与录制、上传，所有资源均来自网络。
      </p>
    </div>
  </div>
</template>

<style scoped>
:deep(.el-input__inner) {
  height: 48px;
}

:deep(.el-input__wrapper) {
  box-shadow: none;
}

:deep(.el-input-group__prepend) {
  box-shadow: none;
}

:deep(.el-input) {
  --el-input-focus-border: transparent;
  --el-input-border-color: transparent;
  --el-input-focus-border-color: transparent;
  --el-input-hover-border-color: transparent;
}

:deep(.el-input-group--prepend .el-input-group__prepend .el-select .el-input.is-focus .el-input__wrapper) {
  box-shadow: none !important;
}

:deep(.el-input-group--prepend .el-input-group__prepend .el-select .el-input .el-input__inner) {
  text-align: center;
}

:deep(.el-select .el-input__wrapper.is-focus) {
  box-shadow: none !important;
}
</style>