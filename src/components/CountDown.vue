<template>
  <div>
    <h1>{{$props.title}}まで</h1>
    <p>
      {{duration.months()}}<span class="unit">ヶ月</span>
      {{duration.days()}}<span class="unit">日</span>
    </p>
    <p>
      {{duration.hours()}}<span class="unit">時間</span>
      {{duration.minutes()}}<span class="unit">分</span>
      {{duration.seconds()}}<span class="unit">秒</span>
      <!-- <span>{{duration.milliseconds()}}</span> -->
    </p>
  </div>
</template>
<script>
import moment from 'moment'
export default {
  name: 'count-down',
  props: {
    title: String,
    dueTime: Date
  },
  data: function () {
    return {
      remainTime: 0,
      counterId: null
    }
  },
  methods: {
    update: function () {
      this.remainTime = this.$props.dueTime.getTime() - new Date().getTime()
    }
  },
  computed: {
    duration: function () {
      return moment.duration(this.remainTime)
    }
  },
  created: function () {
    this.update()
    this.counterId = window.setInterval(() => {
      this.update()
    }, 50)
  },
  beforeDestroy: function () {
    window.clearInterval(this.counterId)
  }
}
</script>
<style scoped>
div {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  border: #2c3e50 2px solid;
  padding: 32px;
  background-color: white;
}

h1 {
  font-size: 5rem;
  margin: 16px;
}

p {
  margin: 0;
  font-size: 4rem;
}

.unit {
  font-size: 50%;
}
</style>
