<script setup>
const props = defineProps({
  search: String,
});
const emit = defineEmits(["update:search"]);
</script>
<template>
  <section class="search-section">
    <form class="search-form" @submit.prevent>
      <label for="search-input">Search</label>
      <input
        id="search-input"
        name="search"
        type="search"
        placeholder="Search by name"
        :value="search"
        @input="emit('update:search', $event.target.value)"
      />
    </form>
  </section>
</template>
