<script setup>
const props = defineProps({
  user: Object,
});
</script>
<template>
  <article class="card">
    <div class="card-top">
      <img
        class="card-image"
        :src="user.image"
        :alt="`${user.firstName} ${user.lastName}`"
      />
      <div class="card-text">
        <h3 class="card-name-group">
          {{ user.firstName }} {{ user.lastName }}
        </h3>
        <p class="card-username">@{{ user.username }}</p>
      </div>
    </div>

    <div class="card-info">
      <span class="label">Email</span>
      <p>{{ user.email }}</p>

      <span class="label">Company</span>
      <p>{{ user.company?.name }}</p>

      <span class="label">City</span>
      <p>{{ user.address?.city }}</p>
    </div>

    <button type="button" class="card-button">View Profile</button>
  </article>
</template>
