<template>
  <div class="login-style">
    <div class="container px-4 py-3 mx-auto">
      <div class="card card0">
        <div class="d-flex flex-lg-row flex-column-reverse">
          <div class="card card1">
            <div class="row justify-content-center my-auto">
              <div class="col-md-8 col-10 my-5">
                <div class="row justify-content-center px-3 mb-3">
                  <img id="logo" src="/img/ngm_logo.gif" alt="logo" />
                </div>
                <h3 class="mb-5 text-center heading">NGM STAFF CONTACTS</h3>
                <h6 class="msg-info text-center">
                  Please login to your account
                </h6>
                <CForm @submit.prevent="loginSubmit">
                  <div class="form-group">
                    <label class="form-control-label text-muted"
                      >Username</label
                    >
                    <input
                      name="username"
                      placeholder="Email"
                      class="form-control"
                      v-model="username"
                    />
                  </div>
                  <div class="form-group">
                    <label class="form-control-label text-muted"
                      >Password</label
                    >
                    <input
                      type="password"
                      name="password"
                      placeholder="Password"
                      class="form-control"
                      v-model="password"
                    />
                  </div>
                  <div class="row justify-content-center my-3 px-3">
                    <button type="submit" class="btn-block btn-color">
                      Login
                    </button>
                  </div>
                </CForm>
                <div class="row justify-content-center my-2">
                  <a @click="navigateToForgot()" style="cursor: pointer"
                    ><small class="text-muted">Forgot Password?</small></a
                  >
                </div>
              </div>
            </div>
          </div>
          <div class="card card2">
            <div class="my-auto mx-md-5 px-md-5 right">
              <h3 class="text-white">
                Welcome to Nallamuthu Gounder Mahalingam College
              </h3>
              <small class="text-white"
                >Nallamuthu Gounder Mahalingam College an Institution engaged in
                providing quality education to the youth has been growing
                consistently spreading its wings far and wide to offer a variety
                of educational programmes under one roof for over 60+ years. To
                provide facilities for higher education for students from high
                schools of Pollachi and Udumalpet Taluks, an organisation called
                “Pollachi Kalvi Kazhagam” was constituted in 1957 under the
                Presidentship of Shri S.P. Nallamuthu Gounder and the
                Secretaryship of Arutchelvar Dr. N. Mahalingam
              </small>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapActions, mapGetters } from "vuex";

export default {
  name: "Login",
  data() {
    return {
      username: "",
      password: ""
    };
  },
  computed: {
    ...mapGetters(["getUserEmail"])
  },
  methods: {
    ...mapActions(["showToast", "login"]),
    loginSubmit() {
      if (this.username && this.password) {
        this.login({
          email: this.username,
          password: this.password
        });
      } else {
        this.showToast({
          class: "bg-danger text-white",
          message: "Please fill the credentials"
        });
      }
    },
    navigateToForgot() {
      this.$router.push("/forgot");
    }
  },
  mounted() {
    if (this.getUserEmail) {
      this.$router.push("/home");
    }
  }
};
</script>
