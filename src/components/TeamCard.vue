<script setup>
const props = defineProps({
  user: Object,
});
</script>
<template>
  <article class="card">
    <div class="card-top">
      <img :src="user.image" :alt="`${user.firstName} ${user.lastName}`" />
      <div>
        <h3>{{ user.firstName }} {{ user.lastName }}</h3>
        <p>@{{ user.username }}</p>
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

    <button type="button">View Profile</button>
  </article>
</template>
