<template>
  <div class="text-sm flex flex-col gap-[4px]">
    <label for="email" class="text-[#666666] text-[14px]">Электронная почта</label>
    <input
      id="email"
      type="mail"
      v-model="email"
      placeholder="Введите эл. почту"
      @blur="validEmail"
      title="Введите корректный email"
      :class= "[ 'h-[40px] border-1 rounded-[12px] pt-[10px] pr-[16px] pb-[10px] pl-[16px] ',
      emailError ? 'border-[#C20000] focus:border-[#C20000]' : 'border-[#E0E0E0] focus:border-[#000000] focus:outline-[#D6D6D6] focus:outline-offset-4'
      ]"

    />
    <p v-if="emailError" class="text-[14px] text-[#C20000]">{{ emailError }}</p>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue'

const props = defineProps({
  modelValue: String,
})

const emit = defineEmits(['update:modelValue'])

const email = ref(props.modelValue || '')
const emailError = ref('')

watch(email, (newVal) => {
  emit('update:modelValue', newVal)
})

const validEmail = () => {
  const reg = /^[^\s@]+@[^\s@]+\.[^\s@]+$/
  if (!email.value || !reg.test(email.value)) {
    emailError.value = 'Недопустимый формат почты'
  } else {
    emailError.value = ''
  }
}

</script>
