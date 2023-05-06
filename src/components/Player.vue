<template>
 
  <tr>
    <td class="name">{{ this.player.name }}</td>
    <td class="score">{{ this.player.points }}</td>
    <td class="buttons">
      <button @click="addPoint()"><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0,0,256,256" width="50px" height="50px" fill-rule="nonzero"><g fill="#fec681" fill-rule="nonzero" stroke="none" stroke-width="1" stroke-linecap="butt" stroke-linejoin="miter" stroke-miterlimit="10" stroke-dasharray="" stroke-dashoffset="0" font-family="none" font-weight="none" font-size="none" text-anchor="none" style="mix-blend-mode: normal"><g transform="scale(5.12,5.12)"><path d="M25,2c-12.6907,0 -23,10.3093 -23,23c0,12.69071 10.3093,23 23,23c12.69071,0 23,-10.30929 23,-23c0,-12.6907 -10.30929,-23 -23,-23zM25,4c11.60982,0 21,9.39018 21,21c0,11.60982 -9.39018,21 -21,21c-11.60982,0 -21,-9.39018 -21,-21c0,-11.60982 9.39018,-21 21,-21zM24.98438,16.98633c-0.55152,0.00862 -0.99193,0.46214 -0.98437,1.01367v6h-6c-0.36064,-0.0051 -0.69608,0.18438 -0.87789,0.49587c-0.18181,0.3115 -0.18181,0.69676 0,1.00825c0.18181,0.3115 0.51725,0.50097 0.87789,0.49587h6v6c-0.0051,0.36064 0.18438,0.69608 0.49587,0.87789c0.3115,0.18181 0.69676,0.18181 1.00825,0c0.3115,-0.18181 0.50097,-0.51725 0.49587,-0.87789v-6h6c0.36064,0.0051 0.69608,-0.18438 0.87789,-0.49587c0.18181,-0.3115 0.18181,-0.69676 0,-1.00825c-0.18181,-0.3115 -0.51725,-0.50097 -0.87789,-0.49587h-6v-6c0.0037,-0.2703 -0.10218,-0.53059 -0.29351,-0.72155c-0.19133,-0.19097 -0.45182,-0.29634 -0.72212,-0.29212z"></path></g></g></svg></button>
      <button @click="removePoint()"><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0,0,256,256" width="50px" height="50px" fill-rule="nonzero"><g fill="#fec681" fill-rule="nonzero" stroke="none" stroke-width="1" stroke-linecap="butt" stroke-linejoin="miter" stroke-miterlimit="10" stroke-dasharray="" stroke-dashoffset="0" font-family="none" font-weight="none" font-size="none" text-anchor="none" style="mix-blend-mode: normal"><g transform="scale(5.12,5.12)"><path d="M25,2c-12.6907,0 -23,10.3093 -23,23c0,12.69071 10.3093,23 23,23c12.69071,0 23,-10.30929 23,-23c0,-12.6907 -10.30929,-23 -23,-23zM25,4c11.60982,0 21,9.39018 21,21c0,11.60982 -9.39018,21 -21,21c-11.60982,0 -21,-9.39018 -21,-21c0,-11.60982 9.39018,-21 21,-21zM13,24v2h24v-2z"></path></g></g></svg></button>
      <button @click="removePlayer()"><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0,0,256,256" width="50px" height="50px" fill-rule="nonzero"><g fill="#fec681" fill-rule="nonzero" stroke="none" stroke-width="1" stroke-linecap="butt" stroke-linejoin="miter" stroke-miterlimit="10" stroke-dasharray="" stroke-dashoffset="0" font-family="none" font-weight="none" font-size="none" text-anchor="none" style="mix-blend-mode: normal"><g transform="scale(5.12,5.12)"><path d="M25,2c-12.69047,0 -23,10.30953 -23,23c0,12.69047 10.30953,23 23,23c12.69047,0 23,-10.30953 23,-23c0,-12.69047 -10.30953,-23 -23,-23zM25,4c11.60953,0 21,9.39047 21,21c0,11.60953 -9.39047,21 -21,21c-11.60953,0 -21,-9.39047 -21,-21c0,-11.60953 9.39047,-21 21,-21zM32.99023,15.98633c-0.26377,0.00624 -0.51439,0.11645 -0.69727,0.30664l-7.29297,7.29297l-7.29297,-7.29297c-0.18827,-0.19353 -0.4468,-0.30272 -0.7168,-0.30274c-0.40692,0.00011 -0.77321,0.24676 -0.92633,0.62377c-0.15312,0.37701 -0.06255,0.80921 0.22907,1.09303l7.29297,7.29297l-7.29297,7.29297c-0.26124,0.25082 -0.36648,0.62327 -0.27512,0.97371c0.09136,0.35044 0.36503,0.62411 0.71547,0.71547c0.35044,0.09136 0.72289,-0.01388 0.97371,-0.27512l7.29297,-7.29297l7.29297,7.29297c0.25082,0.26124 0.62327,0.36648 0.97371,0.27512c0.35044,-0.09136 0.62411,-0.36503 0.71547,-0.71547c0.09136,-0.35044 -0.01388,-0.72289 -0.27512,-0.97371l-7.29297,-7.29297l7.29297,-7.29297c0.29724,-0.28583 0.38857,-0.7248 0.23,-1.10546c-0.15857,-0.38066 -0.53454,-0.62497 -0.94679,-0.61524z"></path></g></g></svg></button>
    </td>

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
@import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap');
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
button svg g{
  fill:#ff56d8;
  transition: 0.5s;
}
.name {
  font-size: 3rem;
  font-family: 'Bebas Neue', cursive;
  color: white;
}

.score {
  font-size: 2em;
  color: #ffe818;
  font-family: 'Press Start 2P', cursive;
  /*floating */
}
tr {
  border-bottom: 1px solid rgba(104,220,226,1);
  padding-bottom: 1rem;
  background-color: black;
  transition: 0.5s;
}
tr:hover{
  background-color: rgba(104,220,226,1);
  -webkit-box-shadow: inset 4px 4px 15px 0px #000000, 5px 5px 15px 5px rgba(0,0,0,0); 
  box-shadow: inset 4px 4px 15px 0px #000000, 5px 5px 15px 5px rgba(0,0,0,0);
  cursor: pointer;

}
.buttons button{
  font-size: 3.2rem;
  color:black;
}
button:hover{
  color: white;
  cursor: pointer;
  
}
svg:hover {
  filter: hue-rotate(180deg);
  -webkit-filter: hue-rotate(180deg);
}
svg:active{
  filter: hue-rotate(90deg);
  -webkit-filter: hue-rotate(90deg);
}
</style>