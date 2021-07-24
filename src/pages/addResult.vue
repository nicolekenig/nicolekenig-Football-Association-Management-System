<template>
  <div class="container">
    <h1 class="title">Add Result to Game</h1>
    <h4 class="alert" v-if="token">Sory Threre Were  Problem, Try Again Please</h4>
    <h4 class="alert" v-if="flagConfirm">Result Added </h4>

    <b-form @submit.prevent="onRegister" @reset.prevent="onReset">
      <b-form-group
        id="input-group-game_ID"
        label-cols-sm="3"
        label="game ID:"
        label-for="text"
      >
        <b-form-input
          id="game_ID"
          type="text"
          v-model="$v.form.game_ID.$model"
          :state="validateState('game_ID')"
        ></b-form-input>
        <b-form-invalid-feedback v-if="!$v.form.game_ID.required">
          game ID is required
        </b-form-invalid-feedback>
 <b-form-invalid-feedback v-if="!$v.form.game_ID.integer">
          game ID score is Numeric
                  </b-form-invalid-feedback>
      </b-form-group> <!-- end image input -->
     
     
      <b-form-group
        id="input-group-localteam_score"
        label-cols-sm="3"
        label="Local team score:"
        label-for="localteam_score"
      >
        <b-form-input
          id="localteam_score"
          type="text"
          v-model="$v.form.localteam_score.$model"
          :state="validateState('localteam_score')"
        ></b-form-input>
        <b-form-invalid-feedback v-if="!$v.form.localteam_score.required">
          localteam score is required
                  </b-form-invalid-feedback>
        <b-form-invalid-feedback v-if="!$v.form.localteam_score.integer">
          localteam score is Numeric
                  </b-form-invalid-feedback>

      </b-form-group> <!-- end confirmedPassword input -->

         <b-form-group
        id="input-group-visitoreteam_score"
        label-cols-sm="3"
        label="visitore team score:"
        label-for="visitorteam_score"
      >
        <b-form-input
          id="visitoreteam_score"
          type="text"
          v-model="$v.form.visitoreteam_score.$model"
          :state="validateState('visitoreteam_score')"
        ></b-form-input>
        <b-form-invalid-feedback v-if="!$v.form.visitoreteam_score.required">
          localteam score is required
        </b-form-invalid-feedback>

          <b-form-invalid-feedback v-if="!$v.form.visitoreteam_score.integer">
          visitoreteam score is Numeric Field
        </b-form-invalid-feedback>
      </b-form-group> <!-- end confirmedPassword input -->
     


      <b-button type="reset" variant="danger">Reset</b-button>
      <b-button
        type="submit"
        variant="primary"
        style="width:250px;"
        class="ml-5 w-75"
      >Add result</b-button
      >
      <div class="mt-2">
        return to Admin Page
        <router-link to="AdminPage"> AdminPage</router-link>
      </div>
    </b-form>
    <b-alert
      class="mt-2"
      v-if="form.submitError"
      variant="warning"
      dismissible
      show
    >
      addGame failed: {{ form.submitError }}
    </b-alert>
    <!-- <b-card class="mt-3 md-3" header="Form Data Result">
      <pre class="m-0"><strong>form:</strong> {{ form }}</pre>
      <pre class="m-0"><strong>$v.form:</strong> {{ $v.form }}</pre>
    </b-card> -->
  </div>
</template>

<script>
import countries from "../assets/countries";
import {
  required,
  alpha,
  integer,
} from "vuelidate/lib/validators";

export default {
  name: "addGame",
  data() {
    return {
      flagConfirm:false,
      token: false,
      url:"",
      form: {
        game_ID: "",
        localteam_score:"",
        visitoreteam_score:"",
        submitError: undefined,
        flag:false,

      },
      errors: [],
      validated: false
    };
  },
  validations: {
    form: {
     
      localteam_score: {
          required,
          integer
      },

      visitoreteam_score: {
          required,
          integer
      },

      game_ID:{
        required,
        integer
      }
    }
  },
  methods: {
    validateState(param) {
      const { $dirty, $error } = this.$v.form[param];
      return $dirty ? !$error : null;
    },
    validateUrl() {
    let regex = /^(http|https)/;
    if(this.url.length > 3 && !this.url.match(regex)) {
        this.url = 'http://' + this.url;
    }
  },
    async Register() {
       try {
        const response = await this.axios.post(
          "http://localhost:3000/admin/AddResult",
          {
            game_id: this.form.game_ID,
            localteam_score: this.form.localteam_score,
            visitoreteam_score: this.form.visitoreteam_score,
          }
        );
        // console.log(response);
      } catch (err) {
        console.log(err.response);
          this.token=true;
          console.log(this.token);
          this.flag=true;

      }
  
     this.flagConfirm=true;
        console.log(this.token);
        this.form.submitError = err.response.data.message;

    },
    async onRegister() {
      // console.log("register method called");
      this.$v.form.$touch();
      if (this.$v.form.$anyError) {
        return;
      }
      // console.log("register method go");
      await this.Register();
    },
    onReset() {
      this.token=false,
      this.flagConfirm=false,

      this.form = {
        game_ID: "",
        localteam_score:"",
        visitoreteam_score:"",
      };
      this.$nextTick(() => {
        this.$v.$reset();
      });
    }
  }
};
</script>
<style lang="scss" scoped>
.container {
  max-width: 500px;
}
.alert {
  color: red;
}
</style>
