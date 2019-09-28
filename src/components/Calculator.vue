<template>
  <div class="calcualtor">
    <div class="display">{{current || 0}}</div>
    <div @click="clear" class="btn">C</div>
    <div @click="sign" class="btn">+/-</div>
    <div @click="percent" class="btn">%</div>
    <div @click="divide" class="btn operator">÷</div>
    <div @click="append($event,'7')" class="btn">7</div>
    <div @click="append($event,'8')" class="btn">8</div>
    <div @click="append($event,'9')" class="btn">9</div>
    <div @click="times" class="btn operator">x</div>
    <div @click="append($event,'4')" class="btn">4</div>
    <div @click="append($event,'5')" class="btn">5</div>
    <div @click="append($event,'6')" class="btn">6</div>
    <div @click="minus" class="btn operator">-</div>
    <div @click="append($event,'1')" class="btn">1</div>
    <div @click="append($event,'2')" class="btn">2</div>
    <div @click="append($event,'3')" class="btn">3</div>
    <div @click="add" class="btn operator">+</div>
    <div @click="append($event,'0')" class="btn zero">0</div>
    <div @click="dot($event)" class="btn">.</div>
    <div @click="equal($event)" class="btn operator submit">=</div>
  </div>
</template>

<script>
import { setTimeout } from "timers";
export default {
  data() {
    return {
      previous: null,
      current: "",
      operator: () => this.current,
      operatorClicked: false,
      isActive: false
    };
  },
  methods: {
    toggleButton(element) {
      element.classList.toggle("active");
      setTimeout(() => {
        element.classList.toggle("active");
      }, 100);
    },
    clear() {
      this.toggleButton(event.target);
      this.current = "";
    },
    sign() {
      this.toggleButton(event.target);
      this.current =
        this.current.charAt(0) === "-"
          ? this.current.slice(1)
          : `-${this.current}`;
    },
    percent() {
      this.toggleButton(event.target);
      this.current = `${parseFloat(this.current) / 100}`;
    },
    append(event, number) {
      event.target ? this.toggleButton(event.target): void 0;
      this.isActive = !this.isActive;
      if (this.operatorClicked) {
        this.current = "";
        this.operatorClicked = false;
      }
      this.current = `${this.current}${number}`;
    },
    dot() {
      this.toggleButton(event.target);
      if (this.current.indexOf(".") === -1) {
        this.append({},".");
      }
    },
    setPrevious() {
      // this.toggleButton(event.target);
      this.previous = this.current;
      this.operatorClicked = true;
    },
    divide() {
      this.toggleButton(event.target);
      this.operator = (a, b) => a / b;
      this.setPrevious();
    },
    times() {
      this.toggleButton(event.target);
      this.operator = (a, b) => a * b;
      this.setPrevious();
    },
    minus() {
      this.toggleButton(event.target);
      this.operator = (a, b) => a - b;
      this.setPrevious();
    },
    add() {
      this.toggleButton(event.target);
      this.operator = (a, b) => a + b;
      this.setPrevious();
    },
    equal() {
      this.toggleButton(event.target);
      let result = `${this.operator(
        parseFloat(this.current),
        parseFloat(this.previous)
      )}`;

      this.current = result.toString().includes(".")
        ? parseFloat(result).toFixed(2)
        : result;
      this.previous = null;
    }
  }
};
</script>

<style scoped>
.calcualtor {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(48px, auto);
  margin: 0 auto;
  width: 235px;
  font-size: 1.5em;
  justify-content: center;
}

.btn {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #666;
  color: #fff;
  border: 1px solid #333;
}

.btn.active {
  background-color: #333;
}

.display {
  grid-column: 1/5;
  background-color: #333;
  color: #fff;
  border-top-left-radius: 10px;
  border-top-right-radius: 10px;
  height: 85px;
  display: flex;
  justify-content: flex-end;
  align-items: flex-end;
  padding: 0 10px;
  font-size: 1.8em;
}

.operator {
  background-color: #ff9900;
  color: #fff;
}

.zero {
  grid-column: 1/3;
  border-bottom-left-radius: 10px;
}

.submit {
  border-bottom-right-radius: 10px;
}
</style>