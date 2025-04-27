<template>
  <div class="top-0 flex items-center">
    <img src="./img/Frame3.png" class="h-225 w-163 hidden md:block" />
    <div class="flex flex-col w-197 h-225 left-163 p-10 gap-[24px] justify-center ml-[172px]">
      <img src="./img/TextContainer.png" alt="" class="h-45 w-98 gap-24" />
      <form @submit.prevent="handleSubmit" class="w-98 h-36 flex flex-col gap-[10px]">
        <EmailInput />
        <TeamSizeSelect v-model="teamSize" />
        <InvitationCode />
        <SubmitButton />
      </form>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

import EmailInput from './components/EmailInput.vue'
import TeamSizeSelect from './components/TeamSizeSelect.vue'
import InvitationCode from './components/InvitationCode.vue'
import SubmitButton from './components/SubmitButton.vue'

const teamSize = ref('')

const handleSubmit = () => {
  console.log('Форма отправлена')
}
</script>



<style>
 </style>
