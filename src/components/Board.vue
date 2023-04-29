<template>
  <div class="container">
    <table>
      <thead>
        <!-- <Modal v-show="isVisible">
            <tr>
              <td><button @click="addPlayer(playerName)">Adauga</button></td>
              <td><input v-model="playerName" type="text" placeholder="Nume jucator"></td>
            </tr>
          </Modal> -->
        <tr>
          <td><button @click="addPlayer()">Adauga jucator</button></td>
          <td><button @click="deleteTeam()">Sterge echipa</button></td>
          <td><button @click="changeName()">Schimba nume</button></td>
        </tr>
        <tr>
          <th colspan="3">{{ board.team_name }}</th>
        </tr>
        <tr>
          <td>Jucator</td>
          <td>Puncte</td>
        </tr>
      </thead>
      <tbody>
        <!-- <tr v-for="player in board.team_members" :key="points">
          <td>{{ player.name }}</td>
          <td>{{ player.points }}</td>
          <td><button @click="addPoint()">+</button></td>
          <td><button>-</button></td>
        </tr> -->
        <Player v-for="(player,index) in this.players" :key="index" :player="player" :index="index"/>
        <tr>Total: {{ board.team_points }}</tr>
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
        playerName: ref('')
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
            axios.delete(`http://localhost:3000/boards/${this.board.id}`);
            
            this.$parent.boards.pop();
        },
        components: {
            Player,
        },

       async addPlayer(playerName){
          const newPlayerName = prompt("Introduceti numele jucatorului");
          const res =  await axios.post(`http://localhost:3000/team_members/`, {
            teamid: this.board.id,
            name:newPlayerName,
            points:0,
          });
          this.players = [...this.players, res.data];//window.location.reload();            
      },
      async changeName(){
          const newName = prompt("Introduceti noul nume al echipei");
          axios.patch(`http://localhost:3000/boards/${this.board.id}`, {
            team_name: newName,
          });
          window.location.reload();
        }
    },
    components: { Player }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
th,
td {
  padding: 15px;
}
thead {
  color:black;
}
.container{
  background-color: hwb(188 1% 44%);
  padding: 20px;
  border-radius: 10px;
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 2rem;
}
button{
 
}
</style>
