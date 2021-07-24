<template>
    <div class="league-preview">
      <div :title="leagueName" class = ".league-title">
        <b-card-title>League Name: {{this.leagueName}}</b-card-title>
      </div>
      <ul class=".league-content">
        <b-card-text>
        Season: {{ this.season }}
        <br/>
        Stage: {{ this.stage }}
      </b-card-text>
      </ul>
      <!-- <b-card
      img-alt="Image"
      tag="article"
      style="max-width: 20rem;"
      class="mb-2"
    > -->
     
      
      <!-- <b-button href="#" variant="primary">Go somewhere</b-button> -->
    <!-- </b-card> -->
  </div>
</template>

<script>
export default {
 data() {
    return {
      leagueName: String, 
      season: String, 
      stage: String
    };
  },
  methods:{
    async getLeagueDetails(){
      let results;
      try {
        this.axios.defaults.withCredentials=true;
        results = await this.axios.get(
        `http://localhost:3000/league/getDetails`
        );
    } catch (err) {
        console.log("server:"+err.response);
        }
    console.log("results",(results))
    this.leagueName= results.data.league_name;
    this.season = results.data.current_season_name;
    this.stage = results.data.current_stage_name;
    // console.log("results",(this.results))

    },
  },
  beforeMount(){
      this.getLeagueDetails();
    }
  
}
</script>

<style>
.league-preview {
  display: inline-block;
  width: 280px;
  /* height: 200px; */
  position: relative;
  margin: 10px 10px;
  border-style: solid;
  border-radius: 10px;
  border-width: 5px;
  border-color:rgb(44, 89, 116);
  background: rgba(255, 253, 221, 0.6);
  /* background-color: beige; */
  /* opacity:0.5  ; */
}

.league-preview .league-title {
  text-align: center;
  text-transform: uppercase;
  color:  rgb(111, 155, 1/97);
}

.league-preview .league-content {
  width: 100%;
  overflow: hidden;
}

</style>
