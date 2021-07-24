<template>
    <div class="container">
        <h1> <b-icon icon="info-circle"></b-icon> About</h1>
          <div class="about-text">
            <b-textare>
            Nicole Kenigsberg - 316299031, Naor Saraf - 305715781
            <br>
            <b-textare title-tag="h5" class=" h5text-sm font-weight-bold">Assignment-3-3</b-textare>
            <br>
            Link to out github project part 3.3: 
            <a href="#"  class="card-link"> https://github.com/Web-Development-Environments-2021/assignment-3-3-305715781_316299031</a>
            <br>
            Link to out API: 
            <a href="#"  class="card-link"> https://app.swaggerhub.com/apis/naorsa198/simple-inventory_api/1.0.0</a>
            <br>
            <br>
            <b-textare title-tag="h5" class=" h5text-sm font-weight-bold">Assignment-3-2</b-textare>
            <br>
            Link to out github project part 3.2: 
            <a href="#"  class="card-link"> https://github.com/Web-Development-Environments-2021/assignment-3-2-305715781_316299031</a>
            <br>
            <br>
            <b-textare title-tag="h3" class="underlin">About:</b-textare>
            <br>
            To login as the Football Association Representor type:
            <br>
              username: NicoleKenig
            <br>
              password: nicole@26
            <br>
            <br>
            <b-textare title-tag="h3" class="underlin">.env details to login to out DB:</b-textare>
            <br>
              <b-tab>tedious_userName=nicole</b-tab>
            <br>
              tedious_password=rXs4gfk
            <br>
              tedious_server=footballleaguesql.database.windows.net
            <br>
              tedious_database=LeagueDB
            <!-- <br>
              options: { encrypt: true, enableArithAbort: true }
            <br>
              COOKIE_SECRET=shalom
            <br>
              api_token=3hE3qLqssMKTJMEps2Qd3mYyBW43M1UaZyG1FHTAcfcMJIK1jyKGf8lpe4yB -->
            <br>
            <br>
            <b-textare title-tag="h3" class="underlin">We have implemented the bonus part (in 3-2):</b-textare>
            <br>
              add and get user favorite team,player and game
            <br>
              adding game results
            <br>
              adding events to games
              <br>
            <b-textare title-tag="h4" class="text-sm font-weight-bold">Hope you enjoy  <b-icon icon="emoji-laughing"></b-icon></b-textare>
          </b-textare>
        </div>
    </div>
</template>

<script>
    export default {
        name: "About",
    data() {
    return {
      img_url:""
    }
  },
 }


</script>

<style lang="scss" scoped>

.about-text{
  color: rgb(0, 0, 0);
   text-align:left; 
  // position: center;
  /* right:550px */
}
.underlin{
  text-decoration: underline;
}

</style>