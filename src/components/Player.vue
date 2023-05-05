<template>
 
  <tr>
    <td class="name">{{ this.player.name }}</td>
    <td class="score">{{ this.player.points }}</td>
    <td class="buttons"><button @click="addPoint()">+</button><button @click="removePoint()">-</button><button
        @click="removePlayer()">X</button></td>

  </tr>
</template>

<script>
import axios from 'axios';
export default {
  name: "Player",
  props: {
    player: {},
    index: 0,

  },

  methods: {
    async addPoint() {
      await axios.patch(`http://localhost:3000/team_members/${this.player.id}`, {
        points: this.player.points + 1
      });
      this.player.points++

      await axios.patch(`http://localhost:3000/boards/${this.$parent.board.id}`, {
        team_points: this.$parent.board.team_points + 1,
      });
      this.$parent.board.team_points++

    },
    async removePoint() {
      await axios.patch(`http://localhost:3000/team_members/${this.player.id}`, {
        points: this.player.points - 1
      });
      this.player.points--

      axios.patch(`http://localhost:3000/boards/${this.$parent.board.id}`, {
        team_points: this.$parent.board.team_points - 1,
      });
      this.$parent.board.team_points--
    },
    async removePlayer() {
      axios.delete(`http://localhost:3000/team_members/${this.player.id}`);
      this.$parent.players.splice(this.index, 1)
      this.$parent.board.team_points -= this.player.points

    }
  }

}
</script>

<style  scoped>
@import url('https://fonts.cdnfonts.com/css/calculator');


button {
  background-color: transparent; /* Green */
  /* Green */
  border: none;
  color: white;
  padding: 2px 1px;
  text-align: center;
  text-decoration: none;
  display: inline-flex;
  font-size: 3em;
}

.name {
  width: 50%;
}

.score {
  font-size: 3em;
  font-family: 'Calculator', sans-serif;


}</style>