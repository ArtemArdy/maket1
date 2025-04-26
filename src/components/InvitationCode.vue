<template>
  <div class="flex flex-col gap-[10px]">
    <div class="flex items-center">
      <div class="bg-gray-200 h-[1px] flex-1"></div>
      <div class="text-xs">Код-Приглашение</div>
      <div class="bg-gray-200 h-[1px] flex-1"></div>
    </div>
    <div class="flex gap-[8px] justify-center">
      <input
        v-for="(_, index) in 4"
        :key="index"
        type="text"
        maxlength="1"
        pattern="[0-9]"
        v-model="code[index]"
        @input="handleInput(index, $event)"
        class="border-gray-300 border-[1px] w-[86px] h-[64px] rounded-[16px] pt-[16px] pr-[8px] pb-[16px] pl-[8px] text-center text-2xl focus:outline-3 focus:outline-offset-1 focus:outline-double"
      />
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const code = ref(['', '', '', ''])

const handleInput = (index, event) => {
  if (event.target.value && index < 3) {
    document.querySelectorAll('input[type="text"]')[index + 1].focus()
  }
}
</script>
