<template>
  <div class="flex flex-col gap-[16px]">
    <div class="flex items-center gap-[8px]">
      <div class="bg-[#E0E0E0] h-[1px] flex-1"></div>
      <div class="text-xs">Код-Приглашение</div>
      <div class="bg-[#E0E0E0] h-[1px] flex-1"></div>
    </div>
    <div class="flex gap-[16px] justify-between ">
      <input
        v-for="(_, index) in 4"
        :key="index"
        type="text"
        maxlength="1"
        pattern="[0-9]"
        v-model="code[index]"
        @input="handleInput(index, $event)"
        class="border-[#E0E0E0] border-[1px] w-full flex 1 h-[64px] rounded-[16px] pt-[16px] pr-[8px] pb-[16px] pl-[8px] text-center text-2xl focus:border-[#000000] focus:outline-[#D6D6D6] focus:outline-offset-4"
      />
    </div>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue'
const modelValue = defineModel({ type: String, default: '' })
const code = ref(modelValue.value.split('') || ['', '', '', ''])


const handleInput = (index, event) => {
  if (event.target.value && index < 3) {
    document.querySelectorAll('input[type="text"]')[index + 1].focus()
  }
}
watch(code, (newVal) => {
  model.value = newVal.join('')

})

</script>
