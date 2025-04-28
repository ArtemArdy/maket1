<template>
  <div class="flex flex-col gap-[4px]">
    <label for="teamSize" class="text-[#666666] text-[14px]">Размер вашей команды</label>
    <select
      id="teamSize"
      v-model="selectedSize"
      class="w-98 h-10 border-1 rounded-lg border-[#E0E0E0] text-sm pt-[10px] pr-[12px] pb-[10px] pl-[12px] focus:outline-3 focus:outline-offset-1 focus:outline-double"
      :class="{ 'text-gray-400': selectedSize === '' }"
    >
      <option
        v-for="option in options"
        :key="option.value"
        :value="option.value"
        :disabled="option.value === ''"
      >
        {{ option.label }}
      </option>
    </select>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue'

const props = defineProps({
  modelValue: {
    type: String,
    default: '',
  },
})

const emit = defineEmits(['update:modelValue'])

const selectedSize = ref(props.modelValue)
const options = [
  { value: '', label: 'Выберите число участников' },
  { value: '1-3', label: '1-3 человек' },
  { value: '4-8', label: '4-8 человек' },
]

watch(selectedSize, (newVal) => {
  emit('update:modelValue', newVal)
})
</script>
