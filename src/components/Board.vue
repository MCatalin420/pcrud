<template>
  <div class="container">

    <table>
      <thead>
        <tr>

          <th class="team-title" colspan="3">
            <div><button class="op" @click="deleteTeam()"><svg xmlns="http://www.w3.org/2000/svg"
                  xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0,0,256,256" width="50px" height="50px"
                  fill-rule="nonzero">
                  <g fill="red" fill-rule="nonzero" stroke="none" stroke-width="1" stroke-linecap="butt"
                    stroke-linejoin="miter" stroke-miterlimit="10" stroke-dasharray="" stroke-dashoffset="0"
                    font-family="none" font-weight="none" font-size="none" text-anchor="none"
                    style="mix-blend-mode: normal">
                    <g transform="scale(5.12,5.12)">
                      <path
                        d="M25,2c-12.69047,0 -23,10.30953 -23,23c0,12.69047 10.30953,23 23,23c12.69047,0 23,-10.30953 23,-23c0,-12.69047 -10.30953,-23 -23,-23zM25,4c11.60953,0 21,9.39047 21,21c0,11.60953 -9.39047,21 -21,21c-11.60953,0 -21,-9.39047 -21,-21c0,-11.60953 9.39047,-21 21,-21zM32.99023,15.98633c-0.26377,0.00624 -0.51439,0.11645 -0.69727,0.30664l-7.29297,7.29297l-7.29297,-7.29297c-0.18827,-0.19353 -0.4468,-0.30272 -0.7168,-0.30274c-0.40692,0.00011 -0.77321,0.24676 -0.92633,0.62377c-0.15312,0.37701 -0.06255,0.80921 0.22907,1.09303l7.29297,7.29297l-7.29297,7.29297c-0.26124,0.25082 -0.36648,0.62327 -0.27512,0.97371c0.09136,0.35044 0.36503,0.62411 0.71547,0.71547c0.35044,0.09136 0.72289,-0.01388 0.97371,-0.27512l7.29297,-7.29297l7.29297,7.29297c0.25082,0.26124 0.62327,0.36648 0.97371,0.27512c0.35044,-0.09136 0.62411,-0.36503 0.71547,-0.71547c0.09136,-0.35044 -0.01388,-0.72289 -0.27512,-0.97371l-7.29297,-7.29297l7.29297,-7.29297c0.29724,-0.28583 0.38857,-0.7248 0.23,-1.10546c-0.15857,-0.38066 -0.53454,-0.62497 -0.94679,-0.61524z">
                      </path>
                    </g>
                  </g>
                </svg></button>
              
                <button class="op" @click="changeName()"><svg xmlns="http://www.w3.org/2000/svg" x="0px" y="0px" width="50"
                height="50" viewBox="0,0,256,256">
                <g fill="yellow" fill-rule="nonzero" stroke="none" stroke-width="1" stroke-linecap="butt"
                  stroke-linejoin="miter" stroke-miterlimit="10" stroke-dasharray="" stroke-dashoffset="0"
                  font-family="none" font-weight="none" font-size="none" text-anchor="none"
                  style="mix-blend-mode: normal">
                  <g transform="scale(2,2)">
                    <path
                      d="M79.33594,15.66797c-1.27148,-0.0457 -2.56094,0.09414 -3.83594,0.43164c-3.4,0.9 -6.20039,3.09961 -7.90039,6.09961l-3.59961,6.5c-0.8,1.4 -0.30039,3.30156 1.09961,4.10156l17.30078,10c0.5,0.3 1,0.39844 1.5,0.39844c0.3,0 0.49883,0.00039 0.79883,-0.09961c0.8,-0.2 1.40078,-0.70039 1.80078,-1.40039l3.69922,-6.5c1.7,-3 2.20078,-6.49844 1.30078,-9.89844c-0.9,-3.4 -3.09961,-6.20039 -6.09961,-7.90039c-1.875,-1.0625 -3.94531,-1.65625 -6.06445,-1.73242zM60.09766,38.12695c-0.96875,0.07422 -1.89844,0.59766 -2.39844,1.47266l-30.19922,52.40039c-3.4,5.8 -5.29922,12.30039 -5.69922,18.90039l-0.80078,12.90039c-0.1,1.1 0.5,2.19883 1.5,2.79883c0.5,0.3 1,0.40039 1.5,0.40039c0.6,0 1.19922,-0.2 1.69922,-0.5l10.80078,-7.09961c5.5,-3.7 10.2,-8.60039 13.5,-14.40039l30.30078,-52.40039c0.8,-1.4 0.29844,-3.29961 -1.10156,-4.09961c-1.4,-0.8 -3.29961,-0.30039 -4.09961,1.09961l-30.29883,52.40039c-2.9,4.9 -6.90117,9.20039 -11.70117,12.40039l-5.79883,3.79883l0.39844,-6.89844c0.3,-5.7 2.00039,-11.30078 4.90039,-16.30078l30.30078,-52.40039c0.8,-1.4 0.30039,-3.29961 -1.09961,-4.09961c-0.525,-0.3 -1.12188,-0.41758 -1.70312,-0.37305zM49,121c-1.7,0 -3,1.3 -3,3c0,1.7 1.3,3 3,3h40c1.7,0 3,-1.3 3,-3c0,-1.7 -1.3,-3 -3,-3zM104,121c-1.65685,0 -3,1.34315 -3,3c0,1.65685 1.34315,3 3,3c1.65685,0 3,-1.34315 3,-3c0,-1.65685 -1.34315,-3 -3,-3z">
                    </path>
                  </g>
                </g>
              </svg></button>
            </div>

            <h1>{{ board.team_name }}</h1>
            

          </th>
        </tr>
        <tr>
          <td><button class="op" @click="addPlayer()"><svg xmlns="http://www.w3.org/2000/svg" x="0px" y="0px" width="70"
                height="70" viewBox="0 0 128 128">
                <path
                  d="M79.9 77.8C74.8 76 69.5 75 64 75c0 0 0 0 0 0s0 0 0 0c-16.4 0-31.6 8.9-39.7 23.1-.8 1.4-.3 3.3 1.1 4.1.5.3 1 .4 1.5.4 1 0 2.1-.5 2.6-1.5C36.6 88.7 49.8 81 64 81c0 0 0 0 0 0s0 0 0 0c4.7 0 9.4.8 13.8 2.5.3.1.7.2 1 .2 1.2 0 2.4-.7 2.8-2C82.2 80.1 81.4 78.4 79.9 77.8zM64 67c12.7 0 23-10.3 23-23S76.7 21 64 21 41 31.3 41 44 51.3 67 64 67zM64 27c9.4 0 17 7.6 17 17s-7.6 17-17 17-17-7.6-17-17S54.6 27 64 27zM101 86c-11 0-20 9-20 20 0 11 9 20 20 20s20-9 20-20C121 95 112 86 101 86zM108 109h-4v4c0 1.7-1.3 3-3 3s-3-1.3-3-3v-4h-4c-1.7 0-3-1.3-3-3s1.3-3 3-3h4v-4c0-1.7 1.3-3 3-3s3 1.3 3 3v4h4c1.7 0 3 1.3 3 3S109.7 109 108 109z">
                </path>
              </svg></button></td>
          <td colspan="2" class="score">
            <p>SCORE {{ this.board.team_points }}</p>
          </td>
        </tr>
        <tr class="labels">
          <td>PLAYER</td>
          <td>POINTS</td>
          <td>TOOLS</td>
        </tr>
      </thead>
      <tbody>
        <Player v-for="(player, index) in this.players" :key="index" :player="player" :index="index" />

        <tr></tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from 'axios';
import Player from './Player.vue';
import { ref } from 'vue';
import { Modal } from 'usemodal-vue3';


export default {
  name: "BoardComp",
  props: {
    board: {},
  },
  data() {
    return {
      players: [],
      isVisible: ref(false),
      playerName: ref(''),
      totalscore: ref(this.board.team_points),
      fixID: ref(false),
    }
  },
  async created() {
    try {
      const res = await axios.get(`http://localhost:3000/team_members/?teamid=${this.board.id}`);
      this.players = res.data;
      this.count = res.data.count;
    } catch (error) {
      console.log(error);
    }
  },
  methods: {

    async deleteTeam() {

      //make a for loop that loops through this.players 
      //and deletes all the players with the same teamid
      for (let i = 0; i < this.players.length; i++) {
        if (this.players[i].teamid == this.board.id) {
          axios.delete(`http://localhost:3000/team_members/${this.players[i].id}`);
        }
      }
      axios.delete(`http://localhost:3000/boards/${this.board.id}`);

      for (let i = 0; i < this.$parent.boards.length; i++) {
        if (this.$parent.boards[i].id == this.board.id) {
          this.$parent.boards.splice(i, 1);
          fixID = true;

        }
        if (this.fixID) {
          this.$parent.boards[i].id = i - 1;
          axios.patch(`http://localhost:3000/boards/${this.$parent.boards[i].id}`, {
            id: i - 1,
          });

        }
      }
      this.$parent.count = this.$parent.boards.length;

    },

    components: {
      Player,
    },

    async addPlayer() {
      const newPlayerName = prompt("Introduceti numele jucatorului");
      const res = await axios.post(`http://localhost:3000/team_members/`, {
        teamid: this.board.id,
        name: newPlayerName,
        points: 0,
      });
      this.players = [...this.players, res.data]; //window.location.reload();            
    },
    async changeName() {
      const newName = prompt("Introduceti noul nume al echipei");
      axios.patch(`http://localhost:3000/boards/${this.board.id}`, {
        team_name: newName,
      });
      this.$parent.boards[this.$parent.boards.indexOf(this.board)].team_name = newName;
    },
    chooseWinner() {
      this.isVisible.value = true;
    },

  },
  components: { Player }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import url('https://fonts.cdnfonts.com/css/calculator');
@import url('https://fonts.googleapis.com/css2?family=Lobster&family=Press+Start+2P&family=Sigmar&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Anton&display=swap');

.labels {
  font-family: 'Press Start 2P', cursive;
  background: #381838;


}

.team-title {
  font-family: Lobster, cursive;
  color: #fe06af;
  font-size: 1.5rem;
  font-family: 'Anton', sans-serif;
  -webkit-text-stroke: 1px rgb(0, 0, 0);
  text-transform: uppercase;


}


table {
  border-collapse: collapse;
  margin-top: 0;
  width: 500px;


}

thead {
  font-family: 'Press Start 2P', cursive;
  background: rgb(0, 0, 0);
  background: linear-gradient(0deg, rgba(0, 0, 0, 1) 1%, rgba(27, 99, 150, 1) 31%, rgba(104, 220, 226, 1) 100%);


}

.container {

  padding: 0px 0px 0px 0px;
  border-radius: 10px;
  color: hsl(0, 75%, 81%);
  display: flex;
  align-items: top;
  justify-content: center;
  font-size: 1rem;


}

.op {
  size: 0.5rem;
  padding: 15px 0px;
  background-color: transparent;
  width: auto;
  border: none;
  color: #fe06af;
  font-size: 0.8rem;

}

.op svg {
  fill: #00ff0d;
}

.op svg:hover {
  fill: #fe06af;
}

.op:hover {
  color: #ffffff;
  text-decoration: underline;
}

.score {
  color: #ffe818;
  font-size: 1.2rem;
  -webkit-text-stroke: 1px rgb(0, 0, 0);
  text-align: right;
  padding-right: 15px;
  animation-name: floating;
  animation-duration: 3s;
  animation-iteration-count: infinite;
  animation-timing-function: ease-in-out;
  margin-left: 30px;
  margin-top: 5px;
}

@keyframes floating {
  0% {
    transform: translate(0, 0px);
  }

  50% {
    transform: translate(0, 10px);
  }

  100% {
    transform: translate(0, -0px);
  }
}

.close {
  text-align: right;
  padding-right: 15px;
}</style>
