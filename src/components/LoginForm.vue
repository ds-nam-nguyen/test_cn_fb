<template>
  <div>
    <h3>Login Form</h3>
    <br />
    <b-form @submit="onSubmit">
      <b-form-group
        id="input-group-1"
        label="Email:"
        label-for="input-1"
        label-cols-sm="4"
        label-cols-lg="3"
        content-cols-sm
        content-cols-lg="7"
        label-align="right"
      >
        <b-form-input id="input-1" type="email" placeholder="Enter email" required v-model="form.email" />
      </b-form-group>

      <b-form-group
        id="input-group-2"
        label="Password:"
        label-for="text-password"
        label-cols-sm="4"
        label-cols-lg="3"
        content-cols-sm
        content-cols-lg="7"
        label-align="right"
      >
        <b-form-input
          id="text-password"
          type="password"
          aria-describedby="password-help-block"
          required
          v-model="form.password"
        />
      </b-form-group>

      <div>
        <b-button type="submit" variant="primary" class="mr-2">Submit</b-button>
        <ConnectFacebook />
      </div>
    </b-form>
    <b-card class="mt-3" header="Form Data Result">
      <pre class="m-0">{{ form }}</pre>
    </b-card>
  </div>
</template>

<script>
import ConnectFacebook from "./ConnectFacebook.vue";

export default {
  components: {
    ConnectFacebook
  },

  data() {
    return {
      form: {
        email: "",
        password: ""
      }
    };
  },
  methods: {
    onSubmit(event) {
      event.preventDefault();
      alert(JSON.stringify(this.form));
    }
  }
};
</script>