<template>
  <div class="text-sm flex flex-col gap-[4px]">
    <label>Электронная почта</label>
    <input
      type="email"
      placeholder="Введите эл. почту"
      pattern="[a-z0-9._%+-]+@[a-z0-9.-]+\.[a-z]{2,}$"
      title="Введите корректный email"
      class="w-98 h-10 border-1 rounded-lg border-[#E0E0E0] pt-[10px] pr-[12px] pb-[10px] pl-[12px] focus:outline-3 focus:outline-offset-1 focus:outline-double"
    />
  </div>
</template>

<script setup></script>
