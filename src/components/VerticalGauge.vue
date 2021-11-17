<template>
  <div id="gauge">
    <div
      v-for="i in bars"
      :key="i"
      class="bar"
      :class="{ empty: (bars-barsFilled) > i }"
      :style="{ backgroundColor: barColor }"
    >
    </div>
  </div>
</template>

<script>
export default {
  name: 'VerticalGauge',
  props: {
    bars: {
      type: Number,
      required: false,
      default: 6,
    },
    value: {
      type: Number,
      required: true,
      default: 0.6
    }
  },
  data() {
    return {
    }
  },
  computed: {
    barsFilled() {
      return Math.floor(this.bars * this.value);
    },
    barColor() {
      if (this.value > 0.75) {
        return '#0e0'
      } else if (this.value > 0.45) {
        return '#dd0'
      } else {
        return '#e00'
      }
    }
  }
}
</script>

<style scoped style="scss">
#gauge {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 100%;
}

.bar {
  border: 1px solid #444;
  border-radius: 4px;
  background-color: #111;
  margin: 2px 0;
  flex: 1 1 auto;
}
.bar:last-child {
  margin-bottom: 0;
}

.empty {
  /* background-color: #d22; */
  background-color: #111 !important;
}
</style>