<template>
  <div class="card">
    <div class="header" v-if="id != -1">
      Lab machine: <span>{{ id }}</span>
    </div>
    <div class="body" v-if="id != -1">
      <div class="col col-1">
        <VerticalGauge
          style="width: 70%;"
          :value="randomFloat()"
        />
      </div>
      <div class="col col-2">
        <div class="row stat-row">
          Ping: <span>13ms</span>
        </div>
        <div class="row stat-row">
          Latency: <span>4.3s</span>
        </div>
        <div class="row stat-row">
          Uptime: <span>13d 5h</span>
        </div>
        <div class="row history-row">
          <div class="history-box"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import VerticalGauge from './VerticalGauge.vue'

export default {
  name: 'ServerStatus',
  components: { VerticalGauge },
  props: {
    id: {
      type: Number,
      required: true,
    }
  },
  methods: {
    randomFloat() {
      if (Math.random() < 0.2) {
        return Math.random() * 0.5 + 0.5;
      } else {
        return Math.random() * 0.5;
      }
    }
  },
}
</script>

<style scoped style="scss">
.card {
  display: flex;
  flex-direction: column;

  background-color: #1a1a1a;
  padding: 20px;
  width: 200px;
  height: 230px;
  border-radius: 6px;
}

.header {
  border-bottom: 2px solid #666;
  text-align: left;
  padding-bottom: 6px;
  margin-bottom: 14px;
}

.header span {
  font-size: 18px;
  color: #eee;
}

.body {
  display: flex;
  flex: 1 1 auto;
  justify-content: space-between;
}

.col {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  flex: 1 1 auto;
  height: 100%;
}

.col-1 {
  flex: 2 1 auto;
}

.header, .stat-row {
  color: #999;
}
.stat-row span, .header span {
  color: white;
}

.history-row {
  margin-top: 8px;
}

.history-box {
  border: 1px solid #999;
  background-color: #222;
  height: 80px;
}
</style>