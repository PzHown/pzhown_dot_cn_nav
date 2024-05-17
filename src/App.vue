<script setup lang="ts">
import PzLauncher from '@/components/PzLauncher.vue'
import PzFooter from '@/components/PzFooter.vue'
</script>

<template>
  <div class="bg-cyan w-full h-[100dvh] p-8 flex flex-col">
    <div class="flex justify-center pt-16">
      <span class="text-black text-op-20 font-900">PzHown的百宝箱</span>
    </div>
    <div class="grid grid-cols-2 md:grid-cols-6 my-16 gap-4 md:gap-8 max-w-[1280px] self-center">
      <PzLauncher name="DrCom表格转换器" herf="" icon="drlogo.png" />
      <PzLauncher name="DrCom表格转换器1" herf="" icon="drlogo.png" />
      <PzLauncher name="DrCom表格转换器2" herf="" icon="drlogo.png" />

    </div>
    <PzFooter class="pt-16 flex justify-center" />
  </div>
</template>
