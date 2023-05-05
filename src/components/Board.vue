<template>
  <div class="container" >
    <table>
      <thead>
        <tr>
          <th class="team-title" colspan="3"><h1>{{ board.team_name }}</h1></th>
        </tr>
        <tr><td colspan="3" class="score">SCORE {{this.board.team_points}}</td></tr>
        <tr>
          <td><button class="op" @click="addPlayer()">ADD</button></td>
          <td><button class="op" @click="deleteTeam()">DELETE</button></td>
          <td><button class="op" @click="changeName()">EDIT</button></td>
        </tr>
        <tr>
          <td>PLAYER</td>
          <td>POINTS</td>
          <td>TOOLS</td>
        </tr>
      </thead>
      <tbody>
        <Player v-for="(player,index) in this.players" :key="index" :player="player" :index="index"/>
        
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
            for(let i = 0; i < this.players.length; i++){
              if(this.players[i].teamid == this.board.id){
                axios.delete(`http://localhost:3000/team_members/${this.players[i].id}`);
              }
            }
            axios.delete(`http://localhost:3000/boards/${this.board.id}`);
            
            for(let i = 0; i < this.$parent.boards.length; i++){
              if(this.$parent.boards[i].id == this.board.id){
                this.$parent.boards.splice(i,1);
                fixID = true;

              }
              if (this.fixID) {
                this.$parent.boards[i].id = i-1;
                axios.patch(`http://localhost:3000/boards/${this.$parent.boards[i].id}`, {
                  id: i-1,
                });
              
              }
            }
            this.$parent.count = this.$parent.boards.length;
           
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
          this.players = [...this.players, res.data]; //window.location.reload();            
      },
      async changeName(){
          const newName = prompt("Introduceti noul nume al echipei");
          axios.patch(`http://localhost:3000/boards/${this.board.id}`, {
            team_name: newName,
          });
          this.$parent.boards[this.$parent.boards.indexOf(this.board)].team_name = newName;
        }
        
    },
    components: { Player }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import url('https://fonts.cdnfonts.com/css/calculator');
@import url('https://fonts.googleapis.com/css2?family=Lobster&family=Press+Start+2P&family=Sigmar&display=swap');

.team-title {
  font-family: Lobster, cursive;
  color: white;
  font-size:1.5rem;
  
 

}
table {
  border-collapse: collapse;
  margin-top: 0;
  

}

th,td {
  padding: 15px;
  padding-top: 0.8rem;
}
thead {
  font-family: 'Press Start 2P', cursive;
  background: rgb(0,0,0);
  background: linear-gradient(0deg, rgba(0,0,0,1) 1%, rgba(27,99,150,1) 31%, rgba(104,220,226,1) 100%);
  color: rgb(254, 198, 129);
 
}
.container{

  padding: 0px 0px 0px 0px;
  border-radius: 10px;
  color: hsl(0, 0%, 0%);
  display: flex;
  align-items: top;
  justify-content: center;
  font-size: 1rem;
  
}
.op{
 size: 1rem;
 padding: 15px 0px;
 background-color: transparent;
  width: auto;
 border: none;
 color: white;
 font-size: 2rem;
}
.op:hover{
  color:#ff56d8;
  text-decoration: underline;
}
.score {
  color: fuchsia;
  font-size: 1.5rem;
  
}
</style>
