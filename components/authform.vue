<template>
  <v-form v-model="valid">
    <v-text-field v-model="userInfo.name" 
                  label="Name" 
                  :rules="[required('name')]"
                  v-if="hasName" />

    <v-text-field v-model="userInfo.email" 
                  label="Email" 
                  :rules="[required('email'), emailFormat()]"/>

    <v-text-field v-model="userInfo.password"
                  label="Password"
                  :type="showPassword ? 'text' : 'password'" 
                  :append-icon="showPassword ? 'mdi-eye' : 'mdi-eye-off'"
                  @click:append="showPassword = !showPassword"
                  counter=true
                  :rules="[required('password'), minLength('password', 8)]"
                  />
    <b-button type="is-primary" @click="submitForm(userInfo)" :disabled="!valid">{{ buttonText }}</b-button>
    <!-- <v-btn @click="submitForm(userInfo)" :disabled="!valid" color="primary">{{ buttonText }}</v-btn> -->
  </v-form>
</template>

<script>
  import validations from "@/utils/validations";

  export default {
    data() {
      return {
        valid: false,
        showPassword: false,
        userInfo: {
          email: 'helloworld@gmail.com',
          password: 'password'
        },
        ...validations
      }
    },
    props: ["submitForm", "buttonText", "hasName"]
  };
</script>

<style scoped>

</style>