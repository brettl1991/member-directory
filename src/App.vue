<script setup>
import { ref, onMounted, computed } from "vue";
import SearchBar from "./components/SearchBar.vue";
import TeamCard from "./components/TeamCard.vue";

const title = ref("Team Directory");
const subTitle = ref("Browse and search team members");
const users = ref([]);
const search = ref("");
const loading = ref(false);
const error = ref(null);

const fetchUsers = async () => {
  loading.value = true;
  error.value = null;
  try {
    const resp = await fetch("https://dummyjson.com/users");
    if (!resp.ok) throw new Error("Failed to fetch users");
    const data = await resp.json();
    console.log(data);
    users.value = data.users;
  } catch (err) {
    error.value = err.message;
  } finally {
    loading.value = false;
  }
};
onMounted(fetchUsers);
const filteredUsers = computed(() => {
  return users.value.filter((user) => {
    const fullName = `${user.firstName} ${user.lastName}`.toLowerCase();
    return fullName.includes(search.value.toLowerCase());
  });
});
</script>
<template>
  <main>
    <header>
      <h1>{{ title }}</h1>
      <h2>{{ subTitle }}</h2>
    </header>
    <SearchBar :search="search" @update:search="search = $event" />
    <section>
      <p v-if="loading">Loading team members...</p>
      <p v-else-if="error">Something went wrong. Please try again.</p>
      <p v-else-if="filteredUsers.length === 0">No team members found.</p>
      <div v-else>
        <TeamCard v-for="user in filteredUsers" :key="user.id" :user="user" />
      </div>
    </section>
  </main>
</template>
