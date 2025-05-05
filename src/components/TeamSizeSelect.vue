<template>
  <div class="flex flex-col gap-[4px]">
    <label for="teamSize" class="text-[#666666] text-[14px]">Размер вашей команды</label>
     <div class="">
    <div @click="toggleMenu" class=" flex justify-between text-[#999999] h-[40px] w-full border-1 rounded-[12px] border-[#E0E0E0]  text-[14px] pt-[10px] pr-[12px] pb-[10px] pl-[12px] focus:border-[#000000] focus:outline-[#D6D6D6] focus:outline-offset-4">
      <span>{{ selectedOption || 'Выберите количество участников' }}</span>

    <svg xmlns="http://www.w3.org/2000/svg"
       class="h-4 w-4 text-[#999999]" fill="none" viewBox="0 0 24 24" stroke="currentColor">
    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
          d="M19 9l-7 7-7-7" />
  </svg>
    </div>
<div class="relative">
    <div v-if="isOpen" class=" absolute w-full  bg-white border-[#E0E0E0] border-1 rounded-[12px] z-10">
      <ul>
        <li class="py-1 px-2 hover:bg-gray-100 cursor-pointer" @click="selectOption('1 человек')">1 человек</li>
        <li class="py-1 px-2 hover:bg-gray-100 cursor-pointer" @click="selectOption('2-3 человека')">2-3 человека</li>
        <li class="py-1 px-2 hover:bg-gray-100 cursor-pointer" @click="selectOption('4-8 человек')">4-8 человек</li>
      </ul>
    </div>
    </div>
  </div>

  </div>
</template>

<script setup>
import { ref, watch } from 'vue'
const model = defineModel()
const isOpen = ref(false)
const selectedOption = ref(model.value || '')
const toggleMenu = () => {
  isOpen.value = !isOpen.value
}
const selectOption = (option) => {
  selectedOption.value = option
  model.value = option
  isOpen.value = false
}
watch(model, (newVal) => {
  selectedOption.value = newVal
})
</script>
