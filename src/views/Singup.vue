<template>
  <v-container>
    <v-row>
      <v-col>
        <h1>Signup</h1>
        <v-form ref="signUpForm" v-model="formValidity">
          <v-text-field label="Email" type="email" v-model="email"
            :rules="emailRules"
            required
          ></v-text-field>
          <v-autocomplete
            label="Which browser do you use?"
            :items="browsers"
          ></v-autocomplete>
          <v-file-input label="Attach profile picture"></v-file-input>
          <v-date-picker v-model="birthday"></v-date-picker>
          <v-text-field label="Birthday" v-model="birthday" readonly></v-text-field>
          <v-checkbox
            label="Agree to terms & conditions"
            v-model="agreeToTerms"
            :rules="agreeToTermsRules"
            required
            class="mb-4"
          ></v-checkbox>
          <v-btn type="submit" :disabled="!formValidity" class="mr-4" color="primary">Submit</v-btn>
          <v-btn class="mr-4" color="success" @click="validateForm">Validate form</v-btn>
          <v-btn color="warning" class="mr-4" @click="resetValidations">Reset Validation</v-btn>
          <v-btn color="error" @click="resetForm">Reset</v-btn>
        </v-form>
      </v-col>
</v-row>
  </v-container>
</template>

<script>
  export default {
    name: "Singup",
    data: () => ({
      formValidity: false,
      agreeToTerms: false,
      email: '',
      agreeToTermsRules: [
          value => !!value || 'You must agree to the terms and conditions to sign up for an account.'
      ],
      emailRules: [
        value => !!value || 'Email is required.',
        value => value.indexOf('@') !== 0 || 'Email should have a username.',
        value => value.includes('@') || 'Email should include an @ symbol.',
        value => value.indexOf('.') - value.indexOf('@') > 1 || 'Email should contain a valid domain.',
        value => value.indexOf('.') <= value.length - 3 || 'Email should contain a valid domain name extension.',
      ],
      birthday: '',
      browsers: [
          'Chrome',
          'Firefox',
          'Safari',
          'Edge',
          'Brave'
      ]
    }),
    methods: {
      resetForm(){
        this.$refs.signUpForm.reset()
      },
      resetValidations(){
        this.$refs.signUpForm.resetValidation()
      },
      validateForm(){
        this.$refs.signUpForm.validate();
      }
    }
  }
</script>

<style scoped>

</style>