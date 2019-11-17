<template>
  <div class="app flex-row align-items-center">
    <div class="container">
      <b-row class="justify-content-center">
        <b-col md="8">
          <b-card-group>
            <b-card no-body class="p-4">
              <b-card-body>
                <b-form>
                  <h1>Login</h1>
                  <p class="text-muted">Sign In to your account</p>
                  <b-input-group class="mb-3">
                    <b-input-group-prepend><b-input-group-text><i class="icon-user"></i></b-input-group-text></b-input-group-prepend>
                    <b-form-input v-model="email" type="text" class="form-control" placeholder="Email" autocomplete="username email" />
                  </b-input-group>
                  <b-input-group class="mb-4">
                    <b-input-group-prepend><b-input-group-text><i class="icon-lock"></i></b-input-group-text></b-input-group-prepend>
                    <b-form-input v-model="password" type="password" class="form-control" placeholder="Password" autocomplete="current-password" />
                  </b-input-group>
                  <b-row>
                    <b-col cols="6">
                      <b-button variant="primary" @click="getLogin()" class="px-4">Login</b-button>
                    </b-col>
                    <b-col cols="6" class="text-right">
                      <b-button variant="link" class="px-0">Forgot password?</b-button>
                    </b-col>
                  </b-row>
                  <p :hidden="[ visible ? false : true ]" style="color:red;"><small>Credential is not valid.</small></p>
                </b-form>
              </b-card-body>
            </b-card>
            <!-- <b-card no-body class="text-white bg-primary py-5 d-md-down-none" style="width:44%">
              <b-card-body class="text-center">
                <div>
                  <h2>Sign up</h2>
                  <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
                  <b-button variant="primary" class="active mt-3">Register Now!</b-button>
                </div>
              </b-card-body>
            </b-card> -->
          </b-card-group>
        </b-col>
      </b-row>
    </div>
  </div>
</template>

<script>
import DefaultContainer from '../containers/DefaultContainer'
export default {
  name: 'Login',
  components: {
    DefaultContainer
  },
  data() {
    return {
      email: '',
      password: '',
      role: ''
    };
  },
  props:{
    visible: Boolean
  },
  mounted() {
    this.visible = false;
  },
  methods : {
    async getLogin() {
      try {
        const response = await fetch(
          "https://ewms-ruby.herokuapp.com/users/login", {
            method: 'POST',
            body: JSON.stringify({
              "email": this.email,
              "password": this.password
            }),
            headers: { 'Content-type': 'application/json; charset=UTF-8' }
          }
        );
        const data = await response.json();
        if(data != null) {
          if (data.user_role.id === 3) {
            this.$router.push("/dashboard");
            // DefaultContainer.userRole = 'Gudang';
          }
          else if (data.user_role.id === 2) {
            this.$router.push("/dashboardP");
            // DefaultContainer.userRole = 'Peralatan';
          }
          else if (data.user_role.id === 1) {
            this.$router.push("/dashboardM");
            // DefaultContainer.userRole = 'Pemasaran';
          }
        }
        else {
          this.visible=true;
        }
        // this.warehouses = data;
        console.log(data);
      } catch (error) {
        console.error(error);
      }
    },
    login() {
      console.log('login');
      this.$router.push("/dashboard");
    }
  }
}
</script>
