<script setup>
import roadmapData from './assets/data/roadmap';

const productTitle = roadmapData.title;
const roadmapColumns = roadmapData.columns;
</script>

<template>
  <main>
    <div class="roadmap">
      <div class="roadmap__gradient"></div>
      <div class="roadmap__header">
        <!-- Roadmap Title -->
        <h1 class="roadmap__title">{{ productTitle }}</h1>
        <!-- Roadmap Description -->
        <p class="roadmap__description">
          Lorem ipsum dolor sit amet consectetur, adipisicing elit. Velit error
          placeat necessitatibus dignissimos modi perspiciatis esse libero ad
          hic quae.
        </p>
      </div>
      <!-- Roadmap Columns -->
      <div class="roadmap__columns">
        <div
          v-for="column in roadmapColumns"
          :key="column.id"
          class="roadmap__column"
        >
          <!-- Roadmap Column Title -->
          <h2 class="roadmap__column-title">{{ column.title }}</h2>
          <!-- Roadmap Column Cards -->
          <div class="roadmap__column-cards">
            <div v-for="card in column.cards" :key="card.id">
              <div class="roadmap-card">
                <h3 class="roadmap-card__title">{{ card.title }}</h3>
                <p class="roadmap-card__description">{{ card.description }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
.roadmap {
  --roadmap-rhythm: var(--space-l);

  position: relative;
  padding: var(--roadmap-rhythm);
}

.roadmap__gradient {
  position: absolute;
  top: 0;
  left: 0;
  content: '';
  width: 100%;
  height: 0.125rem;
  background: linear-gradient(135deg, var(--blue-base), var(--turqoise-base));
}

.roadmap__header {
  margin-block: var(--space-xl);
}

.roadmap__header > * + * {
  margin-top: var(--roadmap-rhythm);
}

.roadmap__description {
  max-width: 66ch;
}

.roadmap__title {
  font-size: var(--step-3);
  font-weight: var(--font-bold);
}

.roadmap__columns {
  display: grid;
  grid-gap: var(--roadmap-rhythm);
  width: calc(100% + var(--roadmap-rhythm) * 2);
  margin-left: calc(var(--roadmap-rhythm) * -1);
  padding: var(--roadmap-rhythm);
  background: var(--grey-light);
}

.roadmap__column-title {
  font-weight: var(--font-semibold);
  line-height: var(--leading-none);
}

.roadmap__column-cards {
  padding-top: var(--roadmap-rhythm);
}

.roadmap__column-cards > * + * {
  margin-top: var(--roadmap-rhythm);
}

@media (min-width: 48rem) {
  .roadmap__columns {
    grid-template-columns: repeat(3, 1fr);
    grid-gap: var(--space-m);
  }
}
</style>
