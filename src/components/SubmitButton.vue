<template>
  <button
    type="submit"
    :class="[
      'text-[14px] w-full pt-[8px] pr-[12px] pb-[8px] pl-[12px] bg-[#E5E5E5] rounded-[12px] text-amber-50 hover:cursor-pointer hover:bg-[#e5e5e5e8] hover:transition duration-300',
      active ? 'bg-black hover:bg-gray-800 cursor-pointer' : 'bg-[#E5E5E5] cursor-not-allowed',
    ]"
    :disabled="!active"
  >
    <slot>Присоединиться</slot>
  </button>
</template>

<script setup>
defineProps({
  active: Boolean,
})
</script>
