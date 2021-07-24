<template scope="keys">
  <div class="game-table">
    <h2 title-tag="h2" class="titelh2"> <b-icon icon="journals"></b-icon>Curren games in the season</h2> 
    <h4 title-tag="h3" class="titelh3"> 
      <b-input-group id="favorite-input" class="divBox" >Future Games In The season  
      <b-form-input  v-if="this.isLogedin" v-model="addFavorite" placeholder="Game Id" id="box" ></b-form-input>
        <b-button   v-if="this.isLogedin" @click="addToFavorite()" variant="outline-danger"  class="mr-2" >
          <b-icon icon="suit-heart-fill" aria-hidden="true"></b-icon>
          Add Game To Favorite
          </b-button>
    </b-input-group>

    </h4> 

    <b-table sticky-header responsive :items="this.futureG" :fields="futureTableHeadline" :small=true :striped=true :sort-by.sync="sortBy"
      :sort-desc.sync="sortDesc"
      sort-icon-left>
    </b-table>

    <h4 title-tag="h3" class="titelh3">Old Games In The season </h4> 
    <b-table sticky-header responsive  :items="this.oldG" :fields="oldTableHeadline" :small=true :striped=true :sort-by.sync="sortBy"
      :sort-desc.sync="sortDesc"
      sort-icon-left></b-table>

    <br>
    <h4 title-tag="h3" class="titelh3">Old Games Events</h4> 
    <b-table sticky-header responsive :items="this.eventsG" :fields="eventsTableHeadline" :small=true :striped=true :sort-by.sync="sortBy"
      :sort-desc.sync="sortDesc"
      sort-icon-left></b-table>

  </div>
</template>

<script>

  export default {
    label: "SeasonGamesPreview",
    props: {
        futureG:Object,
        oldG: Array,
        eventsG: Object,
        isLogedin: Boolean,
        addFavorite: Number,
        name:String,
    },
    data () { 
      return{
        
          futureTableHeadline: [{ key: 'game_id' ,label:"Game_id"  },{ key: 'localteam',label:"Local Team", sortable: true },{ key: 'vistoreteam',label:"Vistor Team" ,sortable: true }, { key: 'date' ,label:"Date" ,sortable: true}, { key: 'fild' ,label:"Fild"},
           { key: 'mainJudge',label:"Main Judge" }, { key: 'secondaryjudge',label:"Secondary Judge"}],

          oldTableHeadline: [{ key: 'game_id' ,label:"Game_id"  },{ key: 'localteam',label:"Local Team"  ,sortable: true},{ key: 'vistoreteam',label:"Vistor Team" ,sortable: true }, { key: 'date' ,label:"Date" ,sortable: true}, { key: 'fild' ,label:"Fild"},
           { key: 'mainJudge',label:"Main Judge" }, { key: 'secondaryjudge',label:"Secondary Judge"}, { key: 'localteam_score' ,label:"Local Team Score"}, { key: 'visitoreteam_score',label:"Visitor Team Score" }],
          
          eventsTableHeadline: [{ key: 'game_id' ,label:"Game_id"  },{ key: 'date' ,label:"Date" ,sortable: true}, { key: 'minute' ,label:"Minute"}, { key: 'description' ,label:"Description"}],
    // end data

  }},
  methods:{
    async addToFavorite(){
      let response;
      try {
            response = await this.axios.post(
            `http://localhost:3000/users/favoriteGames`,{
              game_id: this.addFavorite
            }
            );
        } catch (err) {
            console.log("server:"+err.response);
            }
        // this.status=response.status;
        console.log("response",(this.response))
        },
    },
    mounted() {
      this.name = this.$route.params.userName;
    },
  }

  
  
</script>

<style lang="scss">
.titelh2{
  padding: inherit;
  color: rgb(0, 168, 70);

}
.titelh3{
    margin-left: 20px; 
}

#favorite-input {
  margin-left: 20px; 
  width: 320px; 
  
}
.mr-2{
  margin-left: 5px;
}

</style>