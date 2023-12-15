<template>
  <div class="forgot-password-page">
    <div class="logo-container">
      <!-- Add your logo here -->
    </div>
    <form @submit.prevent="submit" class="forgot-password-form">
  <h5 class="forgot-password-header" style="font-weight: bold;">Forgot your password? No problem. Just let us know your email address and we will email you a password reset link that will allow you to choose a new one.</h5>

      <div class="form-group">
        <div class="input-field">
          <InputLabel for="email" value="Email" />
          <TextInput
            id="email"
            type="email"
            v-model="form.email"
            required
            autofocus
            autocomplete="username"
          />
          <InputError :message="form.errors.email" />
        </div>
      </div>

      <PrimaryButton :disabled="form.processing" class="forgot-password-button">
        Email Password Reset Link
      </PrimaryButton>

      <div class="links">
        <Link :href="route('login')" style="font-weight: bold; color: yourOriginalColor;">
          <span style="color: white;">Already a member?</span> <span style="color: yourOriginalColor;">Log in.</span>
        </Link>
      </div>
    </form>
  </div>
</template>

<script setup>
import GuestLayout from '@/Layouts/GuestLayout.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';
import { Head, Link, useForm } from '@inertiajs/vue3';

defineProps({
    status: {
        type: String,
    },
});

const form = useForm({
    email: '',
});

const submit = () => {
    form.post(route('password.email'));
};
</script>

<style scoped>
.forgot-password-page {
  background-color: #738fa7;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  color: white;
}

.logo-container {
  width: 300px;
  height: 300px;
  background-color: #071330;
  border-radius: 50%;
  margin-bottom: 20px;
}

.forgot-password-form {
  background-color: #c3ceda;
  padding: 20px;
  border-radius: 25px;
  color: black;
  width: 700px;
  max-width: 80%;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
}

.input-field label {
  font-size: 20px;
   margin-top: 20px;
}

.form-group {
  display: flex;
  flex-direction: column;
}

.input-field {
  display: flex;
  flex-direction: column;
  margin-bottom: 1px;
  border-radius: 10px;
}

.input-field input {
  height: 50px;
  padding: 10px;
  border-radius: 10px;
  font-size: 20px;
}

.forgot-password-button {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin-top: 20px;
  font-size: 20px;
  background-color: #071330;
  height: 50px;
  border-radius: 10px;
}

.forgot-password-button:hover {
  background-color: #0c2c49;
}

.links {
  margin-top: 20px;
  text-align: center;
}

.links span {
  margin: 0 5px;
}
</style>
