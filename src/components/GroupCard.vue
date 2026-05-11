<template>
  <div class="group-card">
    <h2 class="group-title">Group {{ group.id }}</h2>
    <ul class="team-list">
      <li v-for="team in group.teams" :key="team" class="team-item">{{ team }}</li>
    </ul>
  </div>
</template>

<script setup>
defineProps({
  group: {
    type: Object,
    required: true
  }
})
</script>

<style scoped>
.group-card {
  background: #1a1a2e;
  border: 1px solid #16213e;
  border-radius: 8px;
  padding: 1rem;
}
.group-title {
  color: #e94560;
  margin: 0 0 0.75rem;
  font-size: 1.2rem;
  border-bottom: 2px solid #e94560;
  padding-bottom: 0.4rem;
}
.team-list {
  list-style: none;
  padding: 0;
  margin: 0;
}
.team-item {
  padding: 0.35rem 0;
  color: #eee;
  font-size: 0.95rem;
}
.team-item::before {
  content: '⚽ ';
  font-size: 0.8rem;
}
</style>
