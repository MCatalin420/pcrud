<template>
  <img alt="scoreboard" class="logo" src="./assets/logo.png" />
  <div class="headerButtons">
    
    
  </div>

  <div class="BoardsContainer">
    <button class="add" @click="addTeam()">{{ label[0] }}</button>
    <button class="add" @click="choseWinner()">{{ label[1] }}</button>
    <Board ref="boardComponent" v-for="board in this.boards" :key="board.id" :board=board />
  </div>
</template>

<script>
import { ref } from "vue";
import Board from "./components/Board.vue";
import axios from "axios";

export default {
  name: "App",
  data() {
    return {
      boards: [],
      count: ref(0),
      counter: ref(0),
      label: ["<ADD TEAM>","<WINNER>"],
      


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
        team_color: "green",
        team_points: 0,
      });
      

      
      
      console.log(this.count)

      const res = await axios.get(`http://localhost:3000/boards`)
      axios.patch(`http://localhost:3000/boards/${res.data.id}`, {
        team_name: `Team ${this.count}`,
      });
      
      this.boards = res.data;
      this.count = res.data.length;

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

  font-family: 'Sigmar', cursive;

}

button {
  padding: 0 2.5rem 0 3rem;
  transition: 0.5s;

}

button:hover {
  background: transparent;
  color: yellow;
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
  background-image: url("./assets/bg.jpg");
  min-height: 65rem;
}

.BoardsContainer {
  margin: auto;
  margin-top: 0;
  padding: 5rem;
  padding-top: 0;
  
  display: grid;
  grid-template-columns: 30rem 30rem;
  grid-column-gap: 1rem;
  grid-row-gap: 1rem;
  justify-content: center;
}

.add {
  margin: 0 auto;
  font-size: 2.5rem;
  width: -webkit-fill-available;
  color: #5E17EB;
  border:none;
  background: none;
  font-family: 'Press Start 2P', cursive;
  padding: 1rem;
  -webkit-text-stroke: 2px rgba(104, 220, 226, 1);
}

.winnerClass {
  border: 55px solid #fe06af;

}

.logo {

}








@media screen and (max-width: 750px) {
 .BoardsContainer{
  grid-template-columns: 30rem;
 }

}

#app>* {
  max-width: 65rem;
  margin-left: auto;
  margin-right: auto;
}


</style>
