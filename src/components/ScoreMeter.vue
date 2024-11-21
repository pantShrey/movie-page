<template>
  <div class="score-meter">
    <svg viewBox="0 0 36 36" class="circular-chart">
      <path
        class="circle-bg"
        fill="none"
        stroke="#e6e6e6"
        stroke-width="3"
        :d="circlePath"
      />
      <path
        class="circle"
        fill="none"
        :stroke="color"
        stroke-width="3"
        :stroke-dasharray="dashArray"
        :d="circlePath"
      />
      <text x="50%" y="50%" alignment-baseline="middle" text-anchor="middle" class="score-text">
        {{ scoreValue }}
      </text>
    </svg>
    <div class="score-source">{{ score.Source }}</div>
  </div>
</template>

<script>
export default {
  name: 'ScoreMeter',
  props: {
    score: Object
  },
  computed: {
    scoreValue() {
      // Return the score value based on whether it's a fraction or a percentage
      return this.score.Value ? this.score.Value.split('/')[0] : 'N/A';
    },
    scorePercentage() {
      let value = 0;
      let maxValue = 100;

      if (this.score.Value.includes('%')) {
        // If it's a percentage (e.g., "85%")
        value = parseFloat(this.score.Value.split('%')[0]);
      } else if (this.score.Value.includes('/')) {
        // If it's a fraction (e.g., "7.6/10")
        value = parseFloat(this.score.Value.split('/')[0]);
        maxValue = parseFloat(this.score.Value.split('/')[1]);
      }

      // Calculate percentage from either a fraction or a percentage
      return (value / maxValue) * 100;
    },
    color() {
      return '#00bcd4'; // Cyan color for the filled percentage
    },
    dashArray() {
      const radius = 15; // Circle radius
      const circumference = 2 * Math.PI * radius;
      return `${(this.scorePercentage / 100) * circumference} ${circumference}`;
    },
    circlePath() {
      const radius = 15;
      const circumference = 2 * Math.PI * radius;
      return `M 18 2 A 16 16 0 1 1 18 34 A 16 16 0 1 1 18 2`; // Path for the circular chart
    }
  }
};
</script>

<style scoped>
.score-meter {
  position: relative;
  width: 70px;
  height: 70px;
}

.circular-chart {
  width: 100%;
  height: 100%;
}

.circle-bg {
  stroke: #e6e6e6;
}

.circle {
  stroke: #00bcd4; /* Cyan */
  transition: stroke-dasharray 0.3s;
}

.score-text {
  font-size: 8px;
  fill: #fff;
}

.score-source {
  font-size: 10px;
  margin-top: 5px;
  color: white;
}
</style>
