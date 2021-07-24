<template>
    <div>
        <h1 class="title">Your Favorite Next Games</h1>
        <div v-if="results == undefined">
            <h3>You dont have any games in favorite</h3>
        </div>
        <div v-else>
            <FavoriteGamesPreview :gameInfo="results"></FavoriteGamesPreview>
        </div>
        
    </div>
</template>

<script>
import FavoriteGamesPreview from "../components/FavoriteGamesPreview";
export default {
    name :"FavotiteGamePage",
    components:{
        FavoriteGamesPreview
    },
    props:{
        userName: String
    },
    data() {
      return {
          results :Object,
      }
    },
    methods:{
        async getFavoriteGames(results){
            try {
                this.axios.defaults.withCredentials=true;
                const params = {
               name: this.userName
                }
            results = await this.axios.get(
                `http://localhost:3000/game/favoriteGames/${params.name}`
                );
            //  results = await this.axios.get(
            //     `http://localhost:3000/users/favoriteGames`
            //     );
            } catch (err) {
                console.log("server:"+err.response);
                }
            // console.log("results",(results))
            this.status = results.status;
            this.results= results.data;
            // console.log("results",(this.results))
        
            },
        // async updatedUserName() {
        //     console.log("name: ",$route.params.userName)
        //     this.userName = this.$route.params.userName
        // },
    },
    created(){
        if(this.$route.params.userName){
            this.userName = this.$route.params.userName
        }
        // this.userName = this.$root.store.username
        this.getFavoriteGames();
        // console.log("cookies: ",this.$cookies.get("session"));
        // console.log("params", this.$route.params);
        // this.updatedUserName();
    },
}
</script>

<style lang="stylus">

</style>