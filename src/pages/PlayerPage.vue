<template>
  <div class = "card">

  <!-- <b-card

    no-body
    style="max-width: 200rem;"

    img-alt="Image"
    img-top
  >
    <template #header>
      <h4 class="mb-0">{{propObj.name}}</h4>
    </template>


    <b-list-group flush>
      <b-list-group-item>Position: {{propObj.position}}-{{$root.positionKey[propObj.position]}} </b-list-group-item>
      <br>
      <b-list-group-item>Team Name: {{propObj.team_name}} </b-list-group-item>
      <br>
      <img :src="get_image()" />
      <br>
      <b-list-group-item>CommonName: {{propObj.CommonName}} </b-list-group-item> 
      <br>
      <b-list-group-item>nationality: {{propObj.nationality}} </b-list-group-item>
      <br>
      <b-list-group-item>birthdate: {{propObj.birthdate}} </b-list-group-item>
      <br>
      <b-list-group-item>birthcountry: {{propObj.birthcountry}} </b-list-group-item>
      <br>
      <b-list-group-item>height: {{propObj.height}} </b-list-group-item>
      <br>
      <b-list-group-item>weight: {{propObj.weight}} </b-list-group-item> 
    
    </b-list-group>

  </b-card> -->


  <b-card no-body alt="Image placeholder"   img-top class="card-profile">
  <b-row class="justify-content-center">
    <b-col lg="3"  class="order-lg-2">
      <div class="card-profile-image">
        <a href="javascript:;">
          <img :src="get_image()" class="image-circle" alt="Circle image" />
        </a>
      </div>
    </b-col>
  </b-row>
  <b-card-header class="text-center border-0 pt-8 pt-md-4 pb-0 pb-md-4">
    <div class="d-flex justify-content-between">
      <span type="info" size="sm" class="mr-4">Player Profile</span>
    </div>
  </b-card-header>
  <b-card-body class="pt-0">
    <b-row>
      <b-col>
        <div class="card-profile-stats d-flex justify-content-center">
          <div>
            <br>
            <span class="heading"> {{propObj.team_name}} </span>
            <span class="description">Team</span>
          </div>
          <div>
            <br>
            <span class="heading"> {{propObj.position}}</span>
            <span class="description">Position</span>
          </div>
          <div>
            <br>
            <span class="heading">{{$root.positionKey[propObj.position]}}</span>
            <span class="description">Role</span>
          </div>
        </div>
      </b-col>
    </b-row>
    <div class="text-center">
      <h5 class="mb-0">
        {{propObj.name}}<span class="font-weight-light"></span>
      </h5>
      <div class="h5 font-weight-300">
        <i class="ni location_pin mr-2"></i>nationality: {{propObj.nationality}}
      </div>
      <div>
        <i class="ni education_hat mr-2"></i>birthdate: {{propObj.birthdate}}
      </div>
      <div>
        <i class="ni education_hat mr-2"></i>CommonName: {{propObj.CommonName}}
      </div>
      <div>
        <i class="ni education_hat mr-2"></i>birthcountry: {{propObj.birthcountry}}
      </div>
      <div>
        <i class="ni education_hat mr-2"></i>height: {{propObj.height}}
      </div>
      <div>
        <i class="ni education_hat mr-2"></i>weight: {{propObj.weight}}
      </div>
       <hr class="my-4">
        <p>{{propObj.name}} — plays as a {{$root.positionKey[propObj.position]}} at {{propObj.team_name}} team — born ta {{propObj.birthdate}} in  {{propObj.birthcountry}}</p>
    </div>
  </b-card-body>
</b-card>
</div>
</template>

<script>
    export default {  
      data(){
        return{
          propObj: Object
      }
      },

    methods: {
    get_image() {
        if(this.propObj.image != undefined){
        return this.propObj.image;
        }
        else return "'https://cdn.sportmonks.com/images/soccer/placeholder.png"
      }
    },

    mounted() {
      this.propObj=this.$root.store.playerdetail;
      
    },
  }


</script>

<style lang="scss" scoped>
.card{
  
  height: 35rem;
  width: 90rem;
  left: 1%;
  margin-top: 1.5%;
  
}


.card-profile-image {
  position: relative;
   border-radius: 50%;
}

.card-profile-image img {
  position: absolute;
  left: 50%;
  max-width: 180px;
  transition: all .15s ease;
  transform: translate(-50%, -30%);
  border-radius: 50%;
}


.card-profile-stats {
  padding: 1rem 0;
}

.card-profile-stats>div {
  margin-right: 1rem;
  padding: .875rem;
  text-align: center;
}

.card-profile-stats>div:last-child {
  margin-right: 0;
}

.card-profile-stats>div .heading {
  font-size: 1.1rem;
  font-weight: bold;
  display: block;
}

.card-profile-stats>div .description {
  font-size: .875rem;
  color: #adb5bd;
}

.main-content {
  position: relative;
}

.footer {
  padding: 2.5rem 0;
  background: #f7fafc;
}

.footer .copyright {
  font-size: .875rem;
}
.mb-0{
  color: rgb(8, 230, 0);
   font-size: 2rem;
}
</style>