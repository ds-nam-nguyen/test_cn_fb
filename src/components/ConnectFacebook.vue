<template>
  <!-- <div> -->
  <b-button variant="success" @click="logInWithFacebook">Login with Facebook</b-button>
  <!-- </div> -->
</template>
<script>
export default {
  name: "facebookLogin",

  async mounted() {
    await this.loadFacebookSDK(document, "script", "facebook-jssdk");
    await this.initFacebook();
  },

  methods: {
    async logInWithFacebook() {
      if (window.FB) {
        window.FB.login(function (response) {
          if (response.authResponse) {
            alert("You are logged in &amp; cookie set!");
          } else {
            alert("User cancelled login or did not fully authorize.");
          }
        });
        return false;
      }

      return false;
    },
    async initFacebook() {
      window.fbAsyncInit = function () {
        window.FB.init({
          appId: "2975122692770363",
          cookie: true,
          version: "v13.0"
        });
      };
    },
    async loadFacebookSDK(d, s, id) {
      var js,
        fjs = d.getElementsByTagName(s)[0];
      if (d.getElementById(id)) {
        return;
      }
      js = d.createElement(s);
      js.id = id;
      js.src = "https://connect.facebook.net/en_US/sdk.js";
      fjs.parentNode.insertBefore(js, fjs);
    }
  }
};
</script>