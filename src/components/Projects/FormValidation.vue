<script setup>
  import { ref, computed } from 'vue';

  const formData  = ref({
    username: '',
    email: '',
    password: '',
    confirmPassword: ''
  })
  
  const isUsernameValid = computed(() => formData.value.username.trim() !== '')
  const isEmailValid = computed(() => /^[a-zA-Z0-9._%+-]+@gmail\.com$/.test(formData.value.email))
  const isPasswordValid = computed(() => formData.value.password.length >= 8)
  const isConfirmPasswordValid = computed(() => formData.value.password === formData.value.confirmPassword)

  const isFormValid = computed(() => {
    return isUsernameValid.value && isEmailValid.value && isPasswordValid.value && isConfirmPasswordValid.value
  })

  const handleSubmit = () => {
    if(isFormValid.value){
      console.log('Form Submitted: ', formData.value)
    }else{
      console.log('Form is invalid. Please check the form')
    }
  }

</script>

<template>
  <div class="container">
    <div class="form-container">
      <form @submit.prevent="handleSubmit">
        <div class="form-group">
            <label>Username:</label><br>
            <label class="input validator">
              <svg class="h-[1em] opacity-50" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><g stroke-linejoin="round" stroke-linecap="round" stroke-width="2.5" fill="none" stroke="currentColor"><path d="M19 21v-2a4 4 0 0 0-4-4H9a4 4 0 0 0-4 4v2"></path><circle cx="12" cy="7" r="4"></circle></g></svg>
              <input 
              v-model="formData.username"
              type="text" required placeholder="Username"/>
            </label>
            <span class="validator-hint" v-if="!isUsernameValid">
              containing only letters, numbers or dash
            </span>
        </div>

        <div class="form-group">
            <label>Email:</label><br>
            <label class="input validator">
              <svg class="h-[1em] opacity-50" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><g stroke-linejoin="round" stroke-linecap="round" stroke-width="2.5" fill="none" stroke="currentColor"><rect width="20" height="16" x="2" y="4" rx="2"></rect><path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"></path></g></svg>
              <input 
              v-model="formData.email"
              type="email" required placeholder="sample@gmail.com"/>
            </label>
            <span class="validator-hint" v-if="!isEmailValid">
              enter valid email address
            </span>
          </div>

          <div class="form-group">
            <label>Password:</label><br>
            <label class="input validator">
              <svg class="h-[1em] opacity-50" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><g stroke-linejoin="round" stroke-linecap="round" stroke-width="2.5" fill="none" stroke="currentColor"><path d="M2.586 17.414A2 2 0 0 0 2 18.828V21a1 1 0 0 0 1 1h3a1 1 0 0 0 1-1v-1a1 1 0 0 1 1-1h1a1 1 0 0 0 1-1v-1a1 1 0 0 1 1-1h.172a2 2 0 0 0 1.414-.586l.814-.814a6.5 6.5 0 1 0-4-4z"></path><circle cx="16.5" cy="7.5" r=".5" fill="currentColor"></circle></g></svg>
              <input 
              v-model="formData.password"
              type="password" required/>
            </label>
            <span class="validator-hint" v-if="!isPasswordValid">
              Must be more than 8 characters
            </span>
          </div>

          <div class="form-group">
            <label>Confirm Password:</label><br>
            <label class="input validator">
              <svg class="h-[1em] opacity-50" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><g stroke-linejoin="round" stroke-linecap="round" stroke-width="2.5" fill="none" stroke="currentColor"><path d="M2.586 17.414A2 2 0 0 0 2 18.828V21a1 1 0 0 0 1 1h3a1 1 0 0 0 1-1v-1a1 1 0 0 1 1-1h1a1 1 0 0 0 1-1v-1a1 1 0 0 1 1-1h.172a2 2 0 0 0 1.414-.586l.814-.814a6.5 6.5 0 1 0-4-4z"></path><circle cx="16.5" cy="7.5" r=".5" fill="currentColor"></circle></g></svg>
              <input 
              v-model="formData.confirmPassword"
              type="password" required/>
            </label>
            <span class="validator-hint" v-if="!isConfirmPasswordValid">
              Must same as the password
            </span>
          </div>

          <div class="">
            <button 
            class="btn btn-primary"
            type="submit" :disabled="!isFormValid">Submit</button>
          </div>
      </form>
    </div>
  </div>
</template>