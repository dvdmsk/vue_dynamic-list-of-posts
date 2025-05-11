<script setup>
import { deleteComment } from "@/api/comments";
const { comment } = defineProps(["comment"]);
const { email, name, body, id } = comment;

const emit = defineEmits(["delete"]);
const handleDelete = async () => {
  emit("delete");
  await deleteComment(id);
};
</script>

<template>
  <article class="message is-small">
    <div class="message-header">
      <a :href="`mailto:${email}`"> {{ name }} </a>
      <button
        type="button"
        class="delete is-small"
        aria-label="delete"
        @click="handleDelete"
      >
        delete button
      </button>
    </div>
    <div class="message-body">{{ body }}</div>
  </article>
</template>
