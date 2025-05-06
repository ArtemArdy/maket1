<template>
  <div class="flex flex-col gap-1">
    <label for="teamSize" class="text-gray-600 text-sm">
      Размер вашей команды
    </label>

    <div class="relative" ref="dropdownRef">
      <button
        id="teamSize"
        type="button"
        class="flex justify-between items-center w-full h-10 px-3 py-2.5 text-sm text-gray-500 border border-gray-200 rounded-xl hover:border-gray-300 focus:outline-none focus:ring-2 focus:ring-gray-200"
        @click="toggleMenu"
        :aria-expanded="isOpen"
        :aria-controls="'teamSizeOptions'"
      >
        <span>{{ model || 'Выберите количество участников' }}</span>
        <img
          :src="ChevronDown"
          alt=""
          class="h-4 w-4"
          :class="{ 'transform rotate-180': isOpen }"
        />
      </button>

      <ul
        v-if="isOpen"
        id="teamSizeOptions"
        class="absolute w-full mt-1 bg-white border border-gray-200 rounded-xl shadow-lg z-10"
      >
        <li
          v-for="option in options"
          :key="option"
          class="px-3 py-2 text-sm text-gray-700 hover:bg-gray-50 cursor-pointer"
          @click="selectOption(option)"
        >
          {{ option }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted, useTemplateRef } from 'vue'
import ChevronDown from '../assets/chevron-down.svg'

const options = [
  '1 человек',
  '2-3 человека',
  '4-8 человек'
]

const model = defineModel()
const isOpen = ref(false)
const dropdownRef = useTemplateRef('dropdownRef')

const toggleMenu = () => {
  isOpen.value = !isOpen.value
}

const selectOption = (option) => {
  model.value = option
  isOpen.value = false
}

// Close dropdown when clicking outside
// На боевых проектах вручную никто это не делает, обычно юзаются готовые наборы комопзаблов типа vueUse (на него ссылается офф дока)
// Но тут вручную

const handleClickOutside = (event) => {
  if (dropdownRef.value && !dropdownRef.value.contains(event.target)) {
    isOpen.value = false
  }
}

onMounted(() => {
  document.addEventListener('click', handleClickOutside)
})

onUnmounted(() => {
  document.removeEventListener('click', handleClickOutside)
})
</script>
