<template>
  <div class="signup-page">
    <div class="logo-container">
      <!-- Add your logo here -->
    </div>
    <form @submit.prevent="submit" class="signup-form">
      <h5 class="signup-header">SIGN UP</h5>
      <div class="form-group">
        <div class="input-field">
          <InputLabel for="name" value="NAME" />
          <TextInput
            id="name"
            type="text"
            v-model="form.name"
            required
            autofocus
          />
          <InputError :message="form.errors.name" />
        </div>

        <div class="input-field">
          <InputLabel for="email" value="EMAIL" />
          <TextInput
            id="email"
            type="email"
            v-model="form.email"
            required
            autocomplete="username"
          />
          <InputError :message="form.errors.email" />
        </div>

        <div class="input-field">
          <InputLabel for="password" value="PASSWORD" />
          <TextInput
            id="password"
            type="password"
            v-model="form.password"
            required
            autocomplete="new-password"
          />
          <InputError :message="form.errors.password" />
        </div>

        <div class="input-field">
          <InputLabel for="password_confirmation" value="CONFIRM PASSWORD" />
          <TextInput
            id="password_confirmation"
            type="password"
            v-model="form.password_confirmation"
            required
            autocomplete="new-password"
          />
          <InputError :message="form.errors.password_confirmation" />
        </div>
      </div>

      <PrimaryButton :disabled="form.processing" class="signup-button">
        SIGN UP
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
    name: '',
    email: '',
    password: '',
    password_confirmation: '',
});

const submit = () => {
    form.post(route('register'), {
        onFinish: () => form.reset('password', 'password_confirmation'),
    });
};
</script>

<style scoped>
  /* Reuse the styling from the login form */
  .signup-page {
    background-color: #738fa7;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    color: white;
  }

  .signup-header {
    color: #071330;
    font-family: Arial, sans-serif;
    text-align: center;
    font-size: 50px;
    font-weight: bold;
  }

 
  .signup-form {
    background-color: #c3ceda;
    padding: 70px;
    border-radius: 25px;
    color: black;
    width: 1080px;
    max-width: 100%;
    box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
  }

  .input-field label {
    font-size: 20px;
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

  .links {
    display: flex;
    justify-content: space-between;
    margin-top: 20px;
  }

  .signup-button {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    margin-top: 20px;
    margin-bottom: auto;
    font-size: 20px;
    background-color: #071330;
    height: 50px;
    border-radius: 10px;
  }

  .signup-button:hover {
    background-color: #0c2c49; 
  }
</style>
