<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <div class="headerButtons">
    <button class="add" @click="addTeam()">Adauga echipa</button>
    <button class="add" @click="choseWinner()">Alege Castigator</button>
  </div>

  <div class="BoardsContainer">
    <Board v-for="board in this.boards" :key="board.id" :board=board />
  </div>
</template>

<script>
import { ref } from "vue";
import Board from "./components/Board.vue";
import axios from "axios";
const boardarray = ref([]);



export default {
  name: "App",
  data() {
    return {
      boards: [],
      count: ref(0),
      counter: ref(0),
      colors: ["lightblue", "orange", "lightgreen", "pink", "yellow", "lightgrey", "lightcoral", "lightcyan", "lightgoldenrodyellow", "lightpink", "lightsalmon"],


    };

  },
  async created() {
    try {
      const res = await axios.get(`http://localhost:3000/boards`);
      this.boards = res.data;
      this.count = this.boards.length;
    } catch (error) {
      console.log(error);
    }

  },
  methods: {

    async addTeam() {
      await axios.post(`http://localhost:3000/boards`, {
        team_name: "Team ",
        team_color: this.colors[this.id],
        team_points: 0,
      });
      const res = await axios.get(`http://localhost:3000/boards/${this.count + 1}`);

      this.boards.push(res.data);
      this.count++;

      axios.patch(`http://localhost:3000/boards/${res.data.id}`, {
        team_name: `Team ${this.count}`,
      });




    },

    async choseWinner() {
      const res = await axios.get(`http://localhost:3000/boards`);
      const max = Math.max.apply(Math, res.data.map(function (o) { return o.team_points; }))
      const winner = res.data.find(o => o.team_points === max);

      alert(`Echipa castigatoare este ${winner.team_name} cu ${winner.team_points} puncte`);
    }
  },
  components: {
    Board,
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Lobster&family=Press+Start+2P&family=Sigmar&display=swap');

.headerButtons {
  display: flex;
  justify-content: space-between;
  margin: rem 2rem;
  margin: auto 80rem;
  font-family: 'Sigmar', cursive;

}

button {
  padding: 0 2.5rem 0 3rem;

}

button:hover {
  background: transparent;
  color: black;
  cursor: pointer;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.BoardsContainer {
  margin: auto;
  margin-top: 0;
  padding: 5rem;
  padding-top: 2%;
  display: grid;
  grid-template-columns: 30rem 30rem;
  grid-column-gap: 5px;
  grid-row-gap: 5px;
  justify-content: center;
}

.add {
  margin: 0 auto;
  display: block;
}

.winnerClass {
  border: 55px solid #fe06af;

}



.btn {
  padding: 0.8rem 1rem 0.7rem;
  border: 0.2rem solid #4d4d4d;
  cursor: pointer;
  text-transform: uppercase;
}

.btn__danger {
  color: #fff;
  background-color: #ca3c3c;
  border-color: #bd2130;
}

.btn__filter {
  border-color: lightgrey;
}

.btn__danger:focus {
  outline-color: #c82333;
}

.btn__primary {
  color: #fff;
  background-color: #000;
}

.btn-group {
  display: flex;
  justify-content: space-between;
}

.btn-group>* {
  flex: 1 1 auto;
}

.btn-group>*+* {
  margin-left: 0.8rem;
}

.label-wrapper {
  margin: 0;
  flex: 0 0 100%;
  text-align: center;
}

[class*="__lg"] {
  display: inline-block;
  width: 100%;
  font-size: 1.9rem;
}

[class*="__lg"]:not(:last-child) {
  margin-bottom: 1rem;
}

@media screen and (min-width: 620px) {
  [class*="__lg"] {
    font-size: 2.4rem;
  }
}

.visually-hidden {
  position: absolute;
  height: 1px;
  width: 1px;
  overflow: hidden;
  clip: rect(1px 1px 1px 1px);
  clip: rect(1px, 1px, 1px, 1px);
  clip-path: rect(1px, 1px, 1px, 1px);
  white-space: nowrap;
}

[class*="stack"]>* {
  margin-top: 0;
  margin-bottom: 0;
}

.stack-small>*+* {
  margin-top: 1.25rem;
}

.stack-large>*+* {
  margin-top: 2.5rem;
}

@media screen and (min-width: 550px) {
  .stack-small>*+* {
    margin-top: 1.4rem;
  }

  .stack-large>*+* {
    margin-top: 2.8rem;
  }
}

/* End global styles */
#app {
  background: blur(50%);
  margin: 2rem 0 4rem 0;
  padding: 1rem;
  padding-top: 0;
  position: relative;
  background: rgba(191, 245, 255, 0.54);
  border-radius: 16px;
  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
  backdrop-filter: blur(6.9px);
  -webkit-backdrop-filter: blur(6.9px);
  border: 1px solid rgba(191, 245, 255, 0.39);
}

@media screen and (min-width: 550px) {
  #app {
    padding: 4rem;
  }
}

#app>* {
  max-width: 50rem;
  margin-left: auto;
  margin-right: auto;
}

#app>form {
  max-width: 100%;
}

#app h1 {
  display: block;
  min-width: 100%;
  width: 100%;
  text-align: center;
  margin: 0;
  margin-bottom: 1rem;
}</style>
