<template>
  <div class="bg-yellow-500 rounded-sm text-center flex justify-center">
    <button
      @click="showToggle"
      class="opacity-40 text-5xl transform transition-all hover:scale-150 hover:opacity-100"
    >
      <ic:round-add />
    </button>
  </div>
</template>
<script setup>
import { showToggle } from "~/helpers/useNotes";
</script>
