<template>
    <div>
   <b-navbar toggleable="lg" type="dark" variant="info">
      <b-navbar-brand :to="{ name: 'main' }" tag ="a" active-class="active" class="nav-link-main" exact><b-icon icon="house"></b-icon>Superliga-Main page</b-navbar-brand>
      
      <b-collapse id="nav-collapse" is-nav>
      <b-navbar-nav>
          <b-nav-item :to="{ name: 'search' }"  tag ="a" active-class="active" class="nav-link" exact><b-icon icon="search"></b-icon>Search</b-nav-item>
          <b-nav-item :to="{ name: 'currSeasonGames' , params:{userName: $root.store.username}}"  tag ="a" active-class="active" class="nav-link" exact><b-icon icon="calendar2-date"></b-icon>Current Season Games</b-nav-item>
          <b-nav-item :to="{ name: 'about' }"  tag ="a" active-class="active" class="nav-link" exact><b-icon icon="info-circle"></b-icon>About</b-nav-item>
          <b-nav-item v-if="$root.store.adminflag" :to="{ name: 'AdminPage' }"  tag ="a" active-class="active" class="nav-link" exact><b-icon icon="person"></b-icon>Admin</b-nav-item>

      </b-navbar-nav>

      <!-- middle aligned nav items -->
      <b-navbar-nav class="ml-auto" v-if="!$root.store.username">
        <b-navbar-brand class="user" >Hello Guest</b-navbar-brand>
        <b-nav-item :to="{ name: 'login' }" tag ="a" active-class="active" class="nav-link" exact><b-icon icon="people"></b-icon>Login</b-nav-item>
        <b-nav-item :to="{ name: 'register' }" tag ="a" active-class="active" class="nav-link" exact><b-icon icon="person-plus"></b-icon>Register</b-nav-item>
      </b-navbar-nav>
    
      
      <b-navbar-nav class="ml-auto" v-else>
      <!-- Put profile picrure here  ---------------------------------->
      <img class="picture" :src="get_image()"/>
        <b-navbar-brand class="user" >   Welecom back {{$root.store.username}} </b-navbar-brand>
        <b-nav-item-dropdown text="Personal" right>
          <template #button-content>
            User
          </template>
          <b-dropdown-item :to="{ name: 'favorites' , params:{userName: $root.store.username}}"><b-icon icon="suit-heart-fill"></b-icon> Favorites</b-dropdown-item>
          <b-dropdown-item :to="{ name: 'logout' }"><b-icon icon="power"></b-icon> Log Out</b-dropdown-item>
        </b-nav-item-dropdown>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
    <router-view/>
    </div>
</template>

<script>
    export default {
        name: "NavBar",
    data() {
    return {
      img_url:""
    }
  },
  methods:{
    get_image(){
      return this.$root.store.img
    }
  },

  updated(){
    if($root.store.username){
       this.img_url= $root.store.img
    }
  }
 }
    


</script>

<style lang="scss" scoped>

.user{
  color: rgb(255, 255, 255);
  // text-align:center;
  position: relative;
  right:450px;
  font-size: 28px;

}

.picture{
       height: 70px;
       line-height: 70px;
       left: 550px;
      float: left;

}
.nav-link{
  font-size: 15px;
}
</style>