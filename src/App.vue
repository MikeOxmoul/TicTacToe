<template>
  <div id="app">
    <h1>Tic-Tac-Toe</h1>
    <div class="restart">
    <button @click="resetGame">Restart</button>
    </div>
    <div class="game-board">
      <div class="square" v-for="(square, index) in squares" :key="index" @click="makeMove(index)">
        {{ square }}
      </div>
    </div>
  </div>
</template>

<style>
  .game-board {
    display: flex;
    flex-wrap: wrap;
    width: 305px;
    height: 305px;
    border: 2px solid #333;
  }

  .square {
    width: 100px;
    height: 100px;
    font-size: 48px;
    text-align: center;
    line-height: 100px;
    border: 1px solid #333;
  }

  .restart {
    margin-top: 6%;
    margin-left: -62%;
  }
</style>

<script>
export default {
  data() {
    return {
      squares: new Array(9).fill(null),
      xIsNext: true,
    };
  },
  methods: {
    makeMove(index) {
      if (this.squares[index]) return;
      this.squares.splice(index, 1, this.xIsNext ? "X" : "O");
      this.xIsNext = !this.xIsNext;
    },
    resetGame() {
      this.squares = new Array(9).fill(null);
      this.xIsNext = true;
    },
  },
};
</script>
