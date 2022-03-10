<template>
  <div id="app">
    <main>
      <h1>😍GOOD LUCK😍</h1>
      <div class="numbers-box">
        <template v-if="toggle">
          <div class="numbers-item" v-for="alp in alphList" :key="alp">
            <h2>{{alp}}: </h2>
            <span v-for="num in getNumbers()" :key="num" :class="getColor(num)">
              {{num}}
            </span>
          </div>
        </template>
      </div>
      <button @click="toggle = true">GET NUMBERS</button>
      <div class="clear-btn" @click="toggle = false">CLEAR</div>
    </main>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      toggle: false,
      alphList: ["A", "B", "C", "D", "E"]
    }
  },
  methods: {
    getNumbers() {
      let arr = []
      while(arr.length <= 6) {
        const random = Math.floor(Math.random() * 45) + 1;
        if(arr.every((num)=> num !== random)) {
          arr.push(random);
        }
      }
      return arr;
    },
    getColor (num) {
      if (num <= 10) {
        return "yellow";
      } else if (num <= 20) {
        return "blue";
      } else if (num <= 30) {
        return "red";
      } else if (num <= 40) {
        return "black"
      } else if (num <= 45) {
        return "green"
      } else {
        return "error"
      }
    }
  }
}
</script>

<style>
html, body {
  width: 100%;
  height: 100%;
  margin: 0;
  padding: 0;
  overflow: hidden;
  background: rgb(24, 23, 23);
}

#app {
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  ;
}

.numbers-box {
  width: 480px;
  height: 480px;
  min-height: fit-content;
  max-width: calc(100vw - 48px);
  padding: 24px;
  box-sizing: border-box;
  background: rgba(255, 255, 255, 0.8);
  border-radius: 16px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.numbers-item {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}

button {
  width: 100%;
  height: 48px;
  margin-top: 24px;
  background: gold;
  color: white;
  font-weight: bold;
  font-size: 24px;
  border: none;
  border-radius: 8px;
  cursor: pointer;
}

button:hover {
  background: rgb(219, 187, 2);
}

button:active {
  background: rgb(194, 165, 2);
}

h1 {
  text-align: center;
  font-weight: bolder;
  color: white;
}

h2 {
  margin: 0;
  margin-right: 16px;
  height: 48px;
  line-height: 48px;
}

span {
  display: block;
  width: 48px;
  height: 48px;
  text-align: center;
  line-height: 48px;
  font-size: 24px;
  font-weight: bold;
  border: 1px solid black;
  border-radius: 100%;
  color: white
}

@media screen and (max-width: 560px) {

  .numbers-box {
    height: 320px;
  }

  h2 {
    height: 24px;
    line-height: 24px;
  }

  span {
    width: 24px;
    height: 24px;
    font-size: 16px;
    line-height: 24px;
  }
}

.clear-btn {
  color: white;
  text-align: center;
  margin-top: 16px;
  cursor: pointer;
}

.clear-btn:hover {
  text-decoration: underline;
}

.red {
  background: red;
}
.yellow {
  background: yellow;
  color: black;
}
.green {
  background: green;
}
.blue {
  background: blue;
}
.black {
  background: black;
}
</style>
