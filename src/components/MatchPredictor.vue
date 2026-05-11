<template>
  <div class="match-predictor">
    <div class="match-info">
      <span class="match-date">{{ match.date }}</span>
      <span class="match-group">Group {{ groupId }}</span>
    </div>
    <div class="teams-row">
      <button
        :class="['team-btn', { selected: prediction === 'home' }]"
        @click="$emit('predict', 'home')"
      >
        {{ match.home }}
      </button>
      <span class="vs">vs</span>
      <button
        :class="['team-btn', { selected: prediction === 'away' }]"
        @click="$emit('predict', 'away')"
      >
        {{ match.away }}
      </button>
    </div>
    <button
      :class="['draw-btn', { selected: prediction === 'draw' }]"
      @click="$emit('predict', 'draw')"
    >
      Draw
    </button>
  </div>
</template>

<script setup>
defineProps({
  match: { type: Object, required: true },
  groupId: { type: String, required: true },
  prediction: { type: String, default: null }
})

defineEmits(['predict'])
</script>

<style scoped>
.match-predictor {
  background: #1a1a2e;
  border: 1px solid #16213e;
  border-radius: 8px;
  padding: 1rem;
  margin-top: 1rem;
}
.match-info {
  display: flex;
  justify-content: space-between;
  margin-bottom: 0.6rem;
  font-size: 0.8rem;
  color: #888;
}
.teams-row {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  justify-content: center;
}
.team-btn {
  flex: 1;
  padding: 0.6rem 0.4rem;
  border: 2px solid #0f3460;
  border-radius: 6px;
  background: transparent;
  color: #eee;
  font-size: 0.9rem;
  cursor: pointer;
  transition: all 0.2s;
}
.team-btn:hover {
  background: #0f3460;
}
.team-btn.selected {
  background: #e94560;
  border-color: #e94560;
  color: #fff;
  font-weight: bold;
}
.vs {
  color: #888;
  font-size: 0.85rem;
  flex-shrink: 0;
}
.draw-btn {
  display: block;
  width: 100%;
  margin-top: 0.5rem;
  padding: 0.4rem;
  border: 2px solid #0f3460;
  border-radius: 6px;
  background: transparent;
  color: #eee;
  font-size: 0.85rem;
  cursor: pointer;
  transition: all 0.2s;
}
.draw-btn:hover {
  background: #0f3460;
}
.draw-btn.selected {
  background: #533483;
  border-color: #533483;
  color: #fff;
  font-weight: bold;
}
</style>
