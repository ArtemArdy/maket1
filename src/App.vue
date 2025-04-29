<template>
  <div class="flex h-screen items-center w-full p-3 gap-[12px]">
    <div class="h-full min-w-[540px] max-w-[40%] w-full max-lg:hidden">
      <div class="w-full h-full image rounded-[32px]"></div>
    </div>
    <div class="w-full flex justify-center items-center">
      <div class="p-3 flex justify-center items-center flex-col gap-[24px] max-w-[440px]">
        <WelcomeBlock />
        <form @submit.prevent="handleSubmit" class="flex flex-col gap-[16px]">
          <EmailInput />
          <TeamSizeSelect v-model="teamSize" />
          <div class="mt-[8px]">
            <InvitationCode />
          </div>
          <div class="mt-[8px] w-full">
            <SubmitButton />
          </div>
        </form>
      </div>
    </div>
  </div>
</template>
<style>
.image {
  background-image: url('img/Frame2.png');
  background-repeat: no-repeat;
  background-size: cover;
}
</style>
<script setup>
import EmailInput from './components/EmailInput.vue'
import TeamSizeSelect from './components/TeamSizeSelect.vue'
import InvitationCode from './components/InvitationCode.vue'
import SubmitButton from './components/SubmitButton.vue'
import WelcomeBlock from './components/WelcomeBlock.vue'
</script>
