<template>
  <div class="bg-yellow-500 rounded-sm text-center shadow-xl">
    <div class="flex justify-end space-x-2">
      <button @click="editNote(note)" class="hover:text-green-800">
        <ion-edit class="mt-1" />
      </button>
      <button @click="removeNote($props.note.id)" class="hover:text-red-500">
        <zondicons-close class="mt-1 mr-1" />
      </button>
    </div>
    <h3 class="text-2xl font-thin tracking tracking-wider p-1 space-y-2">
      {{ $props.note.title }}
    </h3>
    <p class="text-sm font-medium mb-6">
      {{ $props.note.content }}
    </p>
  </div>
</template>

<script setup>
import { defineProps, defineEmit } from "vue";
import { remove, showToggle, noteToEdit } from "~/helpers/useNotes";

defineProps({
  note: Object,
  default: {
    id: 0,
    title: "",
    content: "",
  },
});

const emit = defineEmit(["deleted"]);

const removeNote = async (id) => {
  await remove(id);
  emit("deleted");
};

const editNote = (note) => {
  noteToEdit.value = note;
  showToggle();
};
</script>
