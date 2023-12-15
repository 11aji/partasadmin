<template>
  <div class="login-page">
    <div class="logo-container">
      <!-- Add your logo here -->
    </div>
    <form @submit.prevent="submit" class="login-form">
      <h5 class="login-header">LOG IN</h5>
      <div class="form-group">
        <div class="input-field">
          <InputLabel for="email" value="EMAIL" />
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

        <div class="input-field">
          <InputLabel for="password" value="PASSWORD" />
          <TextInput
            id="password"
            type="password"
            v-model="form.password"
            required
            autocomplete="current-password"
          />
          <InputError :message="form.errors.password" />
        </div>
      </div>

 <div class="checkbox-field">
    <Checkbox name="remember" v-model:checked="form.remember" />
    <label for="remember" style="font-weight: bold;">&nbsp;&nbsp;Remember me</label>
    <Link v-if="canResetPassword" :href="route('password.request')" style="font-weight: bold;">
        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbspForgot Password?
    </Link>



        
      </div>

      <PrimaryButton :disabled="form.processing" class="login-button">
      
      LOG IN</PrimaryButton>

      <div class="links">
       
       <Link :href="route('register')" style="font-weight: bold; color: yourOriginalColor;">
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp
    <span style="color: white;">Not a member?</span> <span style="color: yourOriginalColor;">Sign-up.</span>
</Link>

      </div>
    </form>
  </div>
</template>

<script setup>
import Checkbox from '@/Components/Checkbox.vue';
import GuestLayout from '@/Layouts/GuestLayout.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';
import { Head, Link, useForm } from '@inertiajs/vue3';

defineProps({
    canResetPassword: {
        type: Boolean,
    },
    status: {
        type: String,
    },
});

const form = useForm({
    email: '',
    password: '',
    remember: false,
});

const submit = () => {
    form.post(route('login'), {
        onFinish: () => form.reset('password'),
    });
};
</script>

<style scoped>
  .login-page {
    background-color: #738fa7;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    color: white;
  }

  .login-header {
    color: #071330;
    font-family: Arial, sans-serif;
    text-align: center;
    font-size: 50px;
    font-weight: bold;
  }

  .logo-container {
    width: 300px;
    height: 300px;
    background-color: #071330;
    border-radius: 50%;
    margin-bottom: 20px;
  }

  .login-form {
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

  .checkbox-field {
    display: flex;
    align-items: center;
    margin-top: 10px;
    margin-bottom: 10px;
  }
  .checkbox-field input[type="checkbox"] {
    transform: scale(2); 
    margin-right: 5px; 
  }
  .links {
    display: flex;
    justify-content: space-between;
    margin-top: 20px;
  }

  .login-button {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    margin-top: auto;
    margin-bottom: auto;
    font-size: 20px;
    background-color: #071330;
    height: 50px;
    border-radius: 10px;
  }
  


  .login-button:hover {
    background-color: #0c2c49; 
  }
</style>