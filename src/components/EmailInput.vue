<template>
  <div class="text-sm flex flex-col gap-[4px]">
    <label for="email" class="text-[#666666] text-[14px]">Электронная почта</label>
    <input
      id="email"
      type="email"
      v-model="email"
      placeholder="Введите эл. почту"
      @blur="validEmail"
      title="Введите корректный email"
      :class="[
        'h-[40px] border-1 rounded-[12px] pt-[10px] pr-[16px] pb-[10px] pl-[16px] focus:outline-[#D6D6D6] focus:outline-offset-4',
        formValidation.email.isValid ? 'border-[#E0E0E0] focus:border-[#000000]' : 'border-[#C20000] focus:border-[#C20000]'
      ]"
    />
    <p v-if="!formValidation.email.isValid" class="text-[14px] text-[#C20000]">
      {{ formValidation.email.error }}
    </p>
  </div>
</template>

<script setup>
const email = defineModel()
const formValidation = defineModel('formValidation')

const validEmail = () => {
  const reg = /^[^\s@]+@[^\s@]+\.[^\s@]+$/
  if (!email.value || !reg.test(email.value)) {
    formValidation.value.email.error = 'Некорректный формат email'
    formValidation.value.email.isValid = false
  } else {
    formValidation.value.email.error = ''
    formValidation.value.email.isValid = true
  }
}
</script>
