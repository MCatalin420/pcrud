<template>
  <div class="container" >
    <table>
      <thead>
        <tr>
          <th colspan="3">{{ board.team_name }}</th>
        </tr>
        <tr>
          <td><button class="op" @click="addPlayer()"><img src="../assets/icons8-add-male-user.svg"></button>></td>
          <td><button class="op" @click="deleteTeam()"><img src="https://img.icons8.com/pastel-glyph/64/null/trash.png"/></button></td>
          <td><button class="op" @click="changeName()"><img src="https://img.icons8.com/pastel-glyph/64/null/edit--v1.png"/></button></td>
        </tr>
        <tr>
          <td>JUCATOR</td>
          <td>PUNCTE</td>
        </tr>
      </thead>
      <tbody>
        <Player v-for="(player,index) in this.players" :key="index" :player="player" :index="index"/>
        <tr> Score: {{this.board.team_points}} </tr>
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
            //make a for loop that loops through this.players 
            //and deletes all the players with the same teamid
            for(let i = 0; i < this.players.length; i++){
              if(this.players[i].teamid == this.board.id){
                axios.delete(`http://localhost:3000/team_members/${this.players[i].id}`);
              }
            }
            this.$parent.boards.pop();
            this.$parent.count--;
        },
        addTeam() {
            this.$parent.addTeam();
        },
        components: {
            Player,
        },

       async addPlayer(){
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
@import url('https://fonts.cdnfonts.com/css/calculator');
@import url('https://fonts.googleapis.com/css2?family=Lobster&family=Press+Start+2P&family=Sigmar&display=swap');

:root {
  --hovercolor: hsl(0, 100%, 75%);
}
table {
  border-collapse: collapse;
  width: 50%;
  font-family: 'Press Start 2P', cursive;
}
th,
td {
  padding: 15px;
  padding-top: 0.2rem;
}
thead {
  font-family: 'Press Start 2P', cursive;
}
.container{
  background-color: hsla(0, 100%, 59%, 0.353);
  border: #42b983 2px solid;
  padding: 0px 0px 0px 0px;
  border-radius: 10px;
  color: hsl(0, 0%, 0%);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1rem;
  height: 30rem;
  
}
.op{
 size: 1rem;
 padding: 15px 0px;
 background-color: transparent;
  width: auto;
 border: none;
 color: hsl(0, 0%, 0%);
}
.op:hover{
  color : white;
}
</style>
