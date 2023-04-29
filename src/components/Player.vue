<template>
   <tr>
          <td>{{ this.player.name }}</td>
          <td>{{ this.player.points }}</td>
          <td><button @click="addPoint()">+</button><button @click="removePoint()">-</button></td>
          <td><button @click="removePlayer()">X</button></td>
        </tr>
</template>

<script>
import axios from 'axios';
export default {
  name: "Player",
  props: {
    player:{},
    index: 0,
    
  },
  
  methods: {
    async addPoint() {
        await axios.patch(`http://localhost:3000/team_members/${this.player.id}`, {
        points: this.player.points + 1
      });
      this.player.points++
    },
    async removePoint() {
        await axios.patch(`http://localhost:3000/team_members/${this.player.id}`, {
        points: this.player.points - 1
      });
      this.player.points--
    },
    async removePlayer() {
            const res = await axios.delete(`http://localhost:3000/team_members/${this.player.id}`);
            this.$parent.players.splice(this.index, 1);
      
    }
  }
  
}
</script>

<style lang="scss" scoped>

</style>