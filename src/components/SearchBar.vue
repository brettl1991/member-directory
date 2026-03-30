<script setup>
const props = defineProps({
  search: String,
});
const emit = defineEmits(["update:search"]);
</script>
<template>
  <section>
    <form @submit.prevent>
      <label for="search-input"
        >Search<input
          id="search-input"
          name="search"
          placeholder="Search by name"
          type="search"
          :value="search"
          @input="emit('update:search', $event.target.value)"
      /></label>
    </form>
  </section>
</template>
