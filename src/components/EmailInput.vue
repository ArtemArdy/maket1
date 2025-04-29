<template>
  <div class="text-sm flex flex-col gap-[4px]">
    <label for="email" class="text-[#666666] text-[14px]">Электронная почта</label>
    <input
      id="email"
      type="mail"
      placeholder="Введите эл. почту"
      pattern="[a-z0-9._%+-]+@[a-z0-9.-]+\.[a-z]{2,}$"
      title="Введите корректный email"
      class=" h-[40px] border-1 rounded-[12px] border-[#E0E0E0] pt-[10px] pr-[16px] pb-[10px] pl-[16px] focus:border-[#000000] focus:outline-[#D6D6D6] focus:outline-offset-4 "
    />
  </div>
</template>

<script setup></script>
