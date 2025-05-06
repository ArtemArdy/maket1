<template>
  <div class="h-dvh flex flex-col">
    <div class="block lg:h-[64px] lg:hidden overflow-hidden">
      <div class="flex items-center px-[20px] py-[16px]">
        <img src="/src/img/Frame10.png" alt="" />
      </div>
    </div>
    <div class="flex lg:h-full lg:items-center w-full p-3 gap-[12px] flex-1">
      <div class="h-full min-w-[540px] max-w-[40%] w-full max-lg:hidden">
        <div class="w-full h-full image rounded-[32px]"></div>
      </div>

      <div class="w-full flex justify-center items-center">
        <div class="p-3 flex justify-center items-center flex-col gap-[24px] max-w-[440px]">
          <WelcomeBlock />
          <form @submit.prevent="handleSubmit" class="flex flex-col gap-[16px]">
            <EmailInput v-model="email" v-model:formValidation="formValidation" />
            <TeamSizeSelect v-model="selectOption" />
            <div class="mt-[8px]">
              <InvitationCode v-model="code" />
            </div>
            <div class="mt-[8px] w-full">
              <SubmitButton :active="isFormComplete" />
            </div>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
import { ref, computed } from 'vue'
import EmailInput from './components/EmailInput.vue'
import TeamSizeSelect from './components/TeamSizeSelect.vue'
import InvitationCode from './components/InvitationCode.vue'
import SubmitButton from './components/SubmitButton.vue'
import WelcomeBlock from './components/WelcomeBlock.vue'
const email = ref('')
const code = ref('')
const selectOption = ref('')
const formValidation = ref({
  email: {
    error: '',
    isValid: true,
  },
})

const isFormComplete = computed(() => {
  return email.value !== '' && selectOption.value !== '' && formValidation.value.email.isValid
})
</script>
<style>
.image {
  background-image: url('img/Frame2.png');
  background-repeat: no-repeat;
  background-size: cover;
}
</style>
