<template>
  <div class="container" style="background-image:url(http://www.4reallearning.com/wp-content/uploads/2019/07/Premier-League-ball.jpg);
  height:830px;  width:1170px;">
  <!-- table info -->
   <b-card-group deck>
     <!-- left card -->
    <b-card footer-tag="footer" title="" class="main-card">
      <b-card-text class="main-LeagueInfo" > <LeagueInfo></LeagueInfo></b-card-text>
     Next Game:
      <b-card-text class="main-GamePreview"><GamePreview 
      :id="results.game_id" 
      :hostTeam="results.localteam" 
      :guestTeam="results.vistoreteam" 
      :date="results.date"
      :hour="results.locatteam_score" 
      :fild="results.fild" 
      :mainJudge ="results.mainJudge"
      :secondaryjudge="results.secondaryjudge"
      :key="results.id"></GamePreview></b-card-text>
      <!-- <b-button href="#" variant="primary">Go somewhere</b-button> -->
    </b-card>

    <!-- rigth card -->
    <b-card title=""  footer-tag="footer" class="main-card">
      <b-card-text>
        <LoginPage v-if="!$root.store.username"></LoginPage>
        <FavoriteGamePage v-else :userName= "$root.store.username"></FavoriteGamePage>
      </b-card-text>
      <!-- <template #footer>
        <em>Footer Slot</em>
      </template> -->
    </b-card>
  </b-card-group>
   
  </div>
</template>

<script>
import LeagueInfo from "../components/LeagueInfo";
import FavoriteGamePage from "../pages/FavoriteGamePage";
import LoginPage from "../pages/LoginPage";
import GamePreview from "../components/GamePreview";
export default {
  components: {
    LeagueInfo, 
    LoginPage, 
    FavoriteGamePage,
    GamePreview
  },
  data(){
    return{
      results: Object,
      userName :String
    }
  },
  methods:{
    async nextGameInLeague(results){
    try {
         
          results = await this.axios.get(
          `http://localhost:3000/league/getNextScheduleGame`
          );
      } catch (err) {
        console.log("server:"+err.response);
      }
      this.status=results.status
      console.log(this.status);
      console.log(results.data);
      this.results= results.data
      let date = results.data.date.toString().split("T");
      this.results.date= date[0];
      console.log(date);
      date = date[1].split("Z")[0];
      this.results.locatteam_score =date.split(".")[0];
    }
  },
  beforeMount(){
    this.nextGameInLeague()
  }
};
</script>

<style lang="scss" scoped>
.blur {
  -webkit-filter: blur(5px); /* Safari 6.0 - 9.0 */
  filter: blur(2px);
}
::v-deep .blur .recipe-preview {
  pointer-events: none;
  cursor: default;
}
.main-card{
  margin-top: 5%;
  background: rgba(255, 253, 221, 0.75);
}
</style>