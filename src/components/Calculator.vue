<template>
  <div class="calcualtor">
    <div class="btn display">{{current}}</div>
    <div @click="clear" class="btn">C</div>
    <div class="btn">+/-</div>
    <div class="btn">%</div>
    <div class="btn operator">÷</div>
    <div class="btn">7</div>
    <div class="btn">8</div>
    <div class="btn">9</div>
    <div class="btn operator">x</div>
    <div class="btn">4</div>
    <div class="btn">5</div>
    <div class="btn">6</div>
    <div class="btn operator">-</div>
    <div class="btn">1</div>
    <div class="btn">2</div>
    <div class="btn">3</div>
    <div class="btn operator">+</div>
    <div class="btn zero">0</div>
    <div class="btn">.</div>
    <div class="btn operator">=</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      current: 10
    };
  },
  methods: {
    clear(){
      this.current = 0;
    }
  },
};
</script>

<style scoped>
.calcualtor {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
  margin: 0 auto;
  width: 400px;
  font-size: 3em;
}

.btn {
  background-color: #f2f2f2;
  border: 1px solid #999;
}

.display {
  grid-column: 1/5;
  background-color: #333;
  color: #fff;
}

.operator {
  background-color: orange;
  color: #fff;
}

.zero {
  grid-column: 1/3;
}
</style>