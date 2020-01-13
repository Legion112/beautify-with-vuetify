<template>
    <v-card class="mx-auto mt-5" width="400">
        <v-card-title>
            <h1 class="display-1">Login</h1>
        </v-card-title>
        <v-card-text>
            <v-form>
                <v-text-field
                        label="Username"
                        prepend-icon="mdi-account-circle"
                />
                <v-text-field
                        :append-icon="showPassword ? 'mdi-eye' : 'mdi-eye-off'"
                        :type="showPassword ? 'text' : 'password'"
                        @click:append="showPassword = !showPassword"
                        label="Password"
                        prepend-icon="mdi-lock"
                />
            </v-form>
        </v-card-text>
        <v-divider></v-divider>
        <v-card-actions>
            <v-btn color="success">Register</v-btn>
            <v-btn color="info">Login</v-btn>
        </v-card-actions>
    </v-card>
</template>

<script>
  export default {
    name: "Login",
    data: () => ({
      showPassword: false,
    }),
  }
</script>

<style scoped>

</style>