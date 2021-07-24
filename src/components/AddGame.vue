<template>
  <div class="container">
    <h1 class="title">Add Game</h1>
    <h4 class="alert" v-if="token">Sory Threre Were  Problem, Try Again Please</h4>
    <h4 class="alert" v-if="flagConfirm">Game Added </h4>

    <b-form @submit.prevent="onRegister" @reset.prevent="onReset">
      <b-form-group
        id="input-group-localteam"
        label-cols-sm="3"
        label="Localteam Name:"
        label-for="localteam"
      >
        <b-form-input
          id="localteam"
          v-model="$v.form.localteam.$model"
          type="text"
          :state="validateState('localteam')"
        ></b-form-input>
        <b-form-invalid-feedback v-if="!$v.form.localteam.required">
          localteam is required
        </b-form-invalid-feedback>
      </b-form-group> 


      <b-form-group
        id="input-group-vistoreteam"
        label-cols-sm="3"
        label="Vistoreteam Name:"
        label-for="vistoreteam"
      >
        <b-form-input
          id="vistoreteam"
          v-model="$v.form.vistoreteam.$model"
          type="text"
          :state="validateState('vistoreteam')"
        ></b-form-input>
        <b-form-invalid-feedback v-if="!$v.form.vistoreteam.required">
          vistoreteam is required
        </b-form-invalid-feedback>
      </b-form-group> 



      <b-form-group
        id="input-group-fild"
        label-cols-sm="3"
        label="Fild:"
        label-for="fild"
      >
        <b-form-input
          id="fild"
          type="text"
          v-model="$v.form.fild.$model"
          :state="validateState('fild')"
        ></b-form-input>
        <b-form-invalid-feedback v-if="!$v.form.fild.required">
          fild is required
        </b-form-invalid-feedback>
         <b-form-invalid-feedback v-if="!$v.form.fild.alpha">
          fild alpha
          </b-form-invalid-feedback>

      </b-form-group> <!-- end last name input -->




        <b-form-group
        id="input-group-mainJudge"
        label-cols-sm="3"
        label="MainJudge:"
        label-for="mainJudge"
      >
        <b-form-input
          id="localteam"
          v-model="$v.form.mainJudge.$model"
          type="text"
          :state="validateState('mainJudge')"
        ></b-form-input>
        <b-form-invalid-feedback v-if="!$v.form.mainJudge.required">
          mainJudge is required
        </b-form-invalid-feedback>
         <b-form-invalid-feedback v-if="!$v.form.mainJudge.alpha">
          mainJudge alpha
          </b-form-invalid-feedback>
      </b-form-group> 

         <b-form-group
        id="input-group-secondaryjudge"
        label-cols-sm="3"
        label="Secondaryjudge:"
        label-for="secondaryjudge"
      >
        <b-form-input
          id="secondaryjudge"
          v-model="$v.form.secondaryjudge.$model"
          type="text"
          :state="validateState('secondaryjudge')"
        ></b-form-input>
        <b-form-invalid-feedback v-if="!$v.form.secondaryjudge.required">
          secondaryjudge is required
        </b-form-invalid-feedback>
         <b-form-invalid-feedback v-if="!$v.form.secondaryjudge.alpha">
          secondaryjudge alpha
          </b-form-invalid-feedback>
      </b-form-group> 

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

      </b-form-group> <!-- end confirmedPassword input -->
      <b-form-group
        id="input-group-date"
        label-cols-sm="3"
        label="Date:"
        label-for="date"
      >
        <b-form-input
          id="date"
          type="date"
          v-model="$v.form.date.$model"
          :state="validateState('date')"
        ></b-form-input>
        <b-form-invalid-feedback v-if="!$v.form.date.required">
          date is required
        </b-form-invalid-feedback>

      </b-form-group> <!-- end image input -->


      <b-button type="reset" variant="danger">Reset</b-button>
      <b-button
        type="submit"
        variant="primary"
        style="width:250px;"
        class="ml-5 w-75"
        >addGame</b-button
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
} from "vuelidate/lib/validators";

export default {
  name: "addGame",
  data() {
    return {
      flagConfirm:false,
      token: false,
      url:"",
      form: {
        localteam:"",
        vistoreteam: "",
        fild: "",
        mainJudge: "",
        secondaryjudge: "",
        date: "",
        localteam_score:"",
        visitoreteam_score:"",
        submitError: undefined,

      },
      errors: [],
      validated: false
    };
  },
  validations: {
    form: {
      localteam: {
        required,
      },

      vistoreteam: {
        required,
      },

      fild: {
        required,
        alpha
      },

      mainJudge: {
        required,
        alpha
      },
      secondaryjudge: {
        required,
        alpha
      },

      localteam_score: {
      },

      visitoreteam_score: {

      },

      date:{
        required,
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
          "http://localhost:3000/admin/AdminAddGame",
          {
            localteam: this.form.localteam,
            vistoreteam: this.form.vistoreteam,
            fild: this.form.fild,
            mainJudge: this.form.mainJudge,
            secondaryjudge: this.form.secondaryjudge,
            date: this.form.date,
            localteam_score: this.form.localteam_score,
            visitoreteam_score: this.form.visitoreteam_score,
          }
        );
        // console.log(response);
      } catch (err) {
        console.log(err.response);
          this.token=true;
          console.log(this.token);
      }
          
          this.flagConfirm=true;
        
        console.log(this.token);
        this.form.submitError = err.response.data.message;

    },
    onRegister() {
      // console.log("register method called");
      this.$v.form.$touch();
      if (this.$v.form.$anyError) {
        return;
      }
      // console.log("register method go");
      this.Register();
    },
    onReset() {
      this.token=false,
      this.flagConfirm=false,

      this.form = {
      localteam:"",
        vistoreteam: "",
        fild: "",
        mainJudge: "",
        secondaryjudge: "",
        confirmedPassword: "",
        date: "",
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
