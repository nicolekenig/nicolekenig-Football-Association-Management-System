<template>
  <div>
    <GamePreview
      v-for="g in gameInfo"
      :id="g.game_id" 
      :hostTeam="g.localteam" 
      :guestTeam="g.vistoreteam" 
      :date="g.date"
      :hour="g.locatteam_score" 
      :fild="g.fild" 
      :mainJudge ="g.mainJudge"
      :secondaryjudge="g.secondaryjudge"
      :key="g.game_id"></GamePreview>
  </div>
</template>

<script>
import GamePreview from "./GamePreview";
export default {
  name: "FavoriteGamesPreview",
  components: {
    GamePreview
  }, 
  props:{
    gameInfo:Object
  },
  // methods: {
  //   async updateGames(){
  //     console.log("response");
  //     try {
  //       const response = await this.axios.get(
  //         "http://localhost:3000/games/favoriteGames",
  //       );
  //       const games = response.data.games;
  //       this.games = [];
  //       this.games.push(...games);
  //       console.log(response);
  //     } catch (error) {
  //       console.log("error in update games")
  //       console.log(error);
  //     }
  //   }
  // }, 
  // mounted(){
  //   console.log("favorite games mounted");
  //   this.updateGames(); 
  // }
};
</script>

<style></style>
