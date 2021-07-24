<template>
  <div class="search">
    <h1 class="title">Search Page</h1>
    <b-input-group prepend="Search Query:" id="search-input" class="divBox">
      <b-form-input v-model="searchQuery"></b-form-input>
        
      <b-form-input v-if="positionFlag===true" v-model="position" placeholder="Position Number">
        <b-input-group-append>
          <b-button @click="startSearch()" variant="success" >Search</b-button>
        </b-input-group-append>
      </b-form-input>

      <b-form-input v-if="filterTeamName===true" v-model="teamName" placeholder="teamname">
        <b-input-group-append>
          <b-button @click="startSearch()" variant="success">Search</b-button>
        </b-input-group-append>
      </b-form-input>


      
      <b-input-group-append>
        <b-button @click="startSearch()" variant="success">Search</b-button>
      </b-input-group-append>

    </b-input-group>

    <br/>
    Your search Query: {{searchQuery }}
    <br>
<div class="divBox">
    <h4> Choose What to Search For : </h4>
     <input class="intput-check" v-if="!teamsearch && !positionFlag  && !filterTeamName" type="checkbox" id="player" value="player" v-model="playersearch">
     <label class="intput-label" v-if="!teamsearch" for="jack">Search player__</label>
        
      <input  class="intput-check" v-if="!playersearch && !positionFlag && !filterTeamName" type="checkbox" id="team" value="team" v-model="teamsearch" >
      <label  class="intput-label"  v-if="!playersearch && !positionFlag  && !filterTeamName" for="john">Search Team</label>
      
      <input  class="intput-check"  v-if="!teamsearch && playersearch" type="checkbox" id="postion" value="position" v-model="positionFlag">
      <label class="intput-label"  v-if="!teamsearch && playersearch" for="jack">Filter By position__</label>

       <input  class="intput-check"  v-if="!teamsearch && playersearch" type="checkbox" id="filterTeamName" value="filterTeamName" v-model="filterTeamName">
      <label  class="intput-label" v-if="!teamsearch && playersearch" for="jack">Filter By Team Name</label>
 </div >           
     
  <br>

<span>Checked names: {{checkedNames}}</span>
<!-- ----------------------------------------------- result search-------------------------- -->

<h1 v-if="emptyResult"> Not Result Found For : {{searchword}} </h1>





<div v-if="playersearch || positionFlag || filterTeamName ">

<span  v-for="res in searchResult" :key="res">
   <router-link to="/PlayerPage" tag="PlayerPreview"  active-class="active" 
      class="card"  @click.native = PlayerDetail(res) >
      <PlayerPreview :propObj="res"></PlayerPreview>
      </router-link>
      
</span>
</div>

<div v-if="teamsearch ">
<span  v-for="(res,index) in searchResultteam" :key="index">
<router-link to="/TeamPage" tag="TeamPreview"  active-class="active" 
      class="card"  @click.native = TeamDetail(res) >

<TeamPreview :propObj="res"></TeamPreview>
</router-link>

</span>
</div>


  <!-- <TeamPreview :propObj="results"></TeamPreview> -->


  </div>

  
</template>

<script>

 import  PlayerPreview from "../components/PlayerPreview";
import  TeamPreview from "../components/TeamPreview";

export default {
  components: { PlayerPreview,TeamPreview },
  //   props:{
  //   anObject: Object
  // },
  data() {
    return {
      searchQuery:"",
      checkedNames:[],
      positionFlag: false,
      playersearch: false,
      teamFlag: false,
      teamsearch: false,
      searchTeamFlag:false,
      filterTeamName: false,
      emptyResult: false,
      position:0,
      teamname:"",
      results: Object,
      resultsteam: Object,
      status:0,
      searchword:"",
    };
  },
  methods:{

  async simpleSearchPlayer(results){
        try {
          let check= [this.searchQuery,this.position,this.teamname]
          console.log(check);
          const params = {
               name:  this.searchQuery,
            };
          results = await this.axios.get(
          `http://localhost:3000/guest/Search/player/${params.name}`
          );
      } catch (err) {
        console.log("server:"+err.response);
        this.flip();
      }
      this.status=results.status
      console.log(this.status);
      console.log(results);
      this.results= results.data
      console.log(this.results)
      if(this.results==0){
        this.flip();
        console.log(this.emptyResult);
      }  
    },

  async filterByPosition(results){
       try {
            let check= [this.searchQuery,this.position,this.teamname]
            console.log(check);
            const params = {
            name:  this.searchQuery,
            position: this.position,
            teamname: this.teamname
            };
            results = await this.axios.get(
          `http://localhost:3000/guest/Search/filter/player/name,${params.name},position,${params.position},teamname,${params.teamname}`

          );
      } catch (err) {
        console.log("server:"+err.response);
      }
       this.status=results.status
      console.log(this.status);
      console.log(results);
      this.results= results.data
      console.log(this.results)
      if(this.results==0){
        this.flip();
        console.log(this.emptyResult);
      }  
    },

    async searchTeam(results){
        try {
          let check= [this.searchQuery]
          console.log(check);
          const params = {
               name:  this.searchQuery,
            };
          results = await this.axios.get(
          `http://localhost:3000/guest/Search/team/${params.name}`
          );
      } catch (err) {
        console.log("server:"+err.response);
//if send error so its empty mean = not result for the user
        this.emptyResult=true;
      }
      try{
      this.resultsteam= results.data
      if(this.resultsteam==0){
        this.flip();
        console.log(this.emptyResult);
      }
      }catch (err){
        this.emptyResult=true;
        console.log(this.emptyResult);
      }
    },


    flip(){
      this.emptyResult=true;
    },
    filpfalse(){
      this.emptyResult=false;
    },
    PlayerDetail(res){
    this.$root.store.toPlayerPage(res);
    },
    TeamDetail(res){
    this.$root.store.toTeamPage(res);
    },

    async startSearch(){
      this.searchword=this.searchQuery;
      console.log(this.playersearch);
       if(this.playersearch || this.positionFlag || this.filterTeamName){
          if(!this.positionFlag && !this.teamFlag){
            await this.simpleSearchPlayer();
          }
          else{
              ( await this.filterByPosition());  
          }
       }
        else if(this.searchTeam){
          await this.searchTeam();
        }
       }
    },

  computed:{
      searchResult(){
          if(this.results.length ===0 ){
           console.log(this.results.length);
          this.flip();
          return [];
          }
        else {
          this.filpfalse()
             return this.results
        }
      },
       searchResultteam(){
          if(this.resultsteam.length ===0 ){
           console.log(this.resultsteam.length);
          this.flip();
          return [];
          }
        else {
                    this.filpfalse()
             return this.resultsteam
        }
      }
  },

  // beforeDestroy() {
  //   this.$root.store.lastSearch(this.searchResult)
  // },        


  // beforeMount() {
  //   if(this.$root.store.results != undefined){
  //     this.startFlag=true
  //   }
  //   this.results = this.$root.store.results;
  // },

  beforeMount() {
    if(this.$root.store.results != undefined){
          this.results = this.$root.store.results;
          this.playersearch=this.$root.store.playersearch;
          this.teamsearch=this.$root.store.teamsearch;
    }
    if(this.$root.store.resultsteam != undefined){
          this.resultsteam = this.$root.store.resultsteam;
          this.playersearch=this.$root.store.playersearch;
          this.teamsearch=this.$root.store.teamsearch;
    }
  
  },

 

  beforeRouteLeave(to ,from ,next){
  this.$root.store.lastSearch(this.searchResult,this.searchResultteam,this.playersearch,this.teamsearch)
  next();
  } 

}
</script>

<style scoped>

.search{
  margin-left: 20px;
}
#search-input {
  margin-left: 20px; 
  width: 500px; 
  
}

.card :hover {
cursor: pointer;
}

/* .title{
  text-align: center
} */

.intput-check  {

display: inline-block;

-webkit-box-shadow: -3px 5px 10px 28px #38BBFF; 
box-shadow: -3px 5px 10px 2px #38BBFF;
background-color: #1C6EA4;
 width: 10px;
 height: 10x;
 color: #FFF;
 padding: 10px;
 content:50px auto 0;
}

/* .divBox{
text-align: center;
} */

.intput-label{
 content: 50px auto 0;

}
</style>