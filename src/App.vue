<template>
  <div class="flex h-screen items-center justify-between">
    <div class="h-full p-3 min-w-[540px] max-w-[40%] w-full max-lg:hidden">
      <div class="w-full h-full image rounded-[32px]">
      </div>
    </div>
    <div class="p-3 w-full flex justify-center items-center flex-col gap-[24px]">
      <handsHi />
      <form @submit.prevent="handleSubmit" class="w-98 h-36 flex flex-col gap-[10px]">
        <EmailInput />
        <TeamSizeSelect v-model="teamSize" />
        <InvitationCode />
        <SubmitButton />
      </form>
    </div>
  </div>
</template>
<style>
.image{
  background-image: url('img/Frame2.png');
  background-repeat: no-repeat;
  background-size: cover;
}
</style>
<script setup>
import EmailInput from './components/EmailInput.vue';
import TeamSizeSelect from './components/TeamSizeSelect.vue';
import InvitationCode from './components/InvitationCode.vue';
import SubmitButton from './components/SubmitButton.vue';
import handsHi from './components/handsHi.vue';

</script>


