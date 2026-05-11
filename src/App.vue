<template>
  <div class="app">
    <header class="header">
      <h1>World Cup 2026 Predictor</h1>
      <p class="subtitle">Predict the results of Matchday 1</p>
    </header>

    <section v-if="predictionsCount > 0" class="summary">
      <p><strong>{{ predictionsCount }}/12</strong> predictions made</p>
      <div class="summary-tags">
        <span
          v-for="(pick, mid) in predictions"
          :key="mid"
          class="tag"
        >
          {{ mid }}: {{ pick === 'draw' ? 'Draw' : pick }}
        </span>
      </div>
      <button class="clear-btn" @click="clearPredictions">Clear All</button>
    </section>

    <div class="groups-grid">
      <div v-for="group in groups" :key="group.id" class="group-section">
        <GroupCard :group="group" />
        <MatchPredictor
          v-for="match in group.matches"
          :key="match.id"
          :match="match"
          :groupId="group.id"
          :prediction="predictions[match.id] || null"
          @predict="(result) => setPrediction(match.id, result)"
        />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import { groups } from './data/groups.js'
import GroupCard from './components/GroupCard.vue'
import MatchPredictor from './components/MatchPredictor.vue'

const STORAGE_KEY = 'wc2026-predictions'

const predictions = ref(loadPredictions())

function loadPredictions() {
  try {
    return JSON.parse(localStorage.getItem(STORAGE_KEY)) || {}
  } catch {
    return {}
  }
}

function savePredictions() {
  localStorage.setItem(STORAGE_KEY, JSON.stringify(predictions.value))
}

function setPrediction(matchId, result) {
  predictions.value[matchId] = result
  predictions.value = { ...predictions.value }
  savePredictions()
}

function clearPredictions() {
  predictions.value = {}
  localStorage.removeItem(STORAGE_KEY)
}

const predictionsCount = computed(() => Object.keys(predictions.value).length)
</script>
