<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <button class="add" @click="addTeam()">Adauga echipa</button>
  <div class="BoardsContainer">
  <Board v-for="board in boards" :key="board.id"  :board=board />
    
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
      boards : [],
      count : ref(0),
    };
  },
  async created() {
    try {
      const res = await axios.get(`http://localhost:3000/boards`);
      this.boards = res.data;
      this.count = res.data.count;
    } catch (error) {
      console.log(error);
    }
  },
  methods: {
    async addTeam() {
      const res = await axios.post(`http://localhost:3000/boards`, {
        team_name:"Team 3",
        team_color: "Red",
        team_points: 0,
      });
      this.boards = [...this.boards, res.data];
    }
  },
  components: {
    Board,
  },
};
</script>

<style>
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
  margin: 20px auto;
  display: grid;
  grid-template-columns: 30rem 30rem;
  grid-column-gap: 20px;
  grid-row-gap: 20px;
  justify-content: center;
}
.add {
    margin:0 auto;
    display:block;
}

</style>
