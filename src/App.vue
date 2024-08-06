<script>
// import { info } from 'autoprefixer';

export default {
  data() {
    return {
      info: [],
      usersGmail:'',
      usersPassword:'',
      showEye: false,
      // emailError: ''
    }
  },
  methods: {
    // validateEmail() {
    //   if (this.email.length < 8) {
    //     this.emailError = 'Email must be at least 8 characters long.';
    //   } else if (!this.email.includes('@') || !this.email.includes('.')) {
    //     this.emailError = 'Email must contain @ and a dot (.)';
    //   } else {
    //     this.emailError = '';
    //   }+
    // },
    // handleSubmit() {
    //   this.validateEmail();
    //   if (!this.emailError) {
    //     alert(`Email: ${this.email}\nPassword: ${this.password}`);
    //   } else {
    //     alert('Please fix the errors in the form.');
    //   }
    // },
    showEyeToggle() {
      this.showEye = !this.showEye;
    },
    // console.log(info)
    infoUsers() {
      this.info.push({
        gmail: this.usersGmail,
        password: this.usersPassword,
      });
      console.log(this.usersGmail)
      console.log(this.usersPassword)
      console.log(this.info)
      // console.log(this.info)
    }
  }
}    
</script>

<template>
  <div class=" min-h-screen min-w-full flex items-center justify-center select-none">
    <div class="bg-white lg:shadow-lg rounded-lg flex overflow-hidden lg:w-auto lg:h-full w-full h-full justify-center p-8 sm:pb-20 sm:pt-20 sm:pr-36 sm:pl-36">
      <!-- <h1 class="text-yellow-500">hello</h1> -->
      <div class="w-full h-full md:w-80">
        <h2 class="text-3xl font-semibold text-gray-900">WELCOME BACK</h2>
      <p class="text-gray-400 mb-8">Welcome back! Please enter your details.</p>
      <form>
        <div class="mb-4">
            <label class="block text-gray-700">Email</label>
            <input v-model="usersGmail" type="email" :class="emailClass" @input="validateEmail" class="w-full px-4 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500" placeholder="Enter your email" required>
            <p v-if="emailError" class="text-red-500 text-sm mt-1">{{ emailError }}</p>
          </div>
          <div class="mb-4 relative">
            <label class="block text-gray-700">Password</label>
            <input :type="showEye ? 'text' : 'password'" v-model="usersPassword" class="w-full px-4 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500" placeholder="********" required>
            <button type="button" @click="togglePasswordVisibility" class="absolute right-3 top-9">
              <svg v-if="showEye" @click="showEyeToggle"  xmlns="http://www.w3.org/2000/svg" width="20px" height="20px" viewBox="0 0 576 512"><path d="M288 32c-80.8 0-145.5 36.8-192.6 80.6C48.6 156 17.3 208 2.5 243.7c-3.3 7.9-3.3 16.7 0 24.6C17.3 304 48.6 356 95.4 399.4C142.5 443.2 207.2 480 288 480s145.5-36.8 192.6-80.6c46.8-43.5 78.1-95.4 93-131.1c3.3-7.9 3.3-16.7 0-24.6c-14.9-35.7-46.2-87.7-93-131.1C433.5 68.8 368.8 32 288 32zM144 256a144 144 0 1 1 288 0 144 144 0 1 1 -288 0zm144-64c0 35.3-28.7 64-64 64c-7.1 0-13.9-1.2-20.3-3.3c-5.5-1.8-11.9 1.6-11.7 7.4c.3 6.9 1.3 13.8 3.2 20.7c13.7 51.2 66.4 81.6 117.6 67.9s81.6-66.4 67.9-117.6c-11.1-41.5-47.8-69.4-88.6-71.1c-5.8-.2-9.2 6.1-7.4 11.7c2.1 6.4 3.3 13.2 3.3 20.3z"/></svg>
              <svg v-else @click="showEyeToggle"  xmlns="http://www.w3.org/2000/svg" width="20px" height="20px" viewBox="0 0 640 512"><path d="M38.8 5.1C28.4-3.1 13.3-1.2 5.1 9.2S-1.2 34.7 9.2 42.9l592 464c10.4 8.2 25.5 6.3 33.7-4.1s6.3-25.5-4.1-33.7L525.6 386.7c39.6-40.6 66.4-86.1 79.9-118.4c3.3-7.9 3.3-16.7 0-24.6c-14.9-35.7-46.2-87.7-93-131.1C465.5 68.8 400.8 32 320 32c-68.2 0-125 26.3-169.3 60.8L38.8 5.1zM223.1 149.5C248.6 126.2 282.7 112 320 112c79.5 0 144 64.5 144 144c0 24.9-6.3 48.3-17.4 68.7L408 294.5c8.4-19.3 10.6-41.4 4.8-63.3c-11.1-41.5-47.8-69.4-88.6-71.1c-5.8-.2-9.2 6.1-7.4 11.7c2.1 6.4 3.3 13.2 3.3 20.3c0 10.2-2.4 19.8-6.6 28.3l-90.3-70.8zM373 389.9c-16.4 6.5-34.3 10.1-53 10.1c-79.5 0-144-64.5-144-144c0-6.9 .5-13.6 1.4-20.2L83.1 161.5C60.3 191.2 44 220.8 34.5 243.7c-3.3 7.9-3.3 16.7 0 24.6c14.9 35.7 46.2 87.7 93 131.1C174.5 443.2 239.2 480 320 480c47.8 0 89.9-12.9 126.2-32.5L373 389.9z"/></svg>

            </button>
          </div>
          <div class="flex items-center justify-between mb-6">
            <label class="flex items-center">
              <input type="checkbox" class="form-checkbox scale-110" required>
              <span class="ml-2 text-gray-700 font-medium">Remember me</span>
            </label>
            <a href="#" class="text-gray-700 font-medium text-xs text-sm text-blue-600 hover:underline">Forgot password</a>
          </div>
          <button @click="infoUsers" class="w-full bg-red-500 text-white py-2 rounded-lg hover:bg-red-600 transition duration-200">Sign in</button>
          <!-- <div class="flex items-center my-6">
            <hr class="flex-grow border-gray-300">
            <span class="mx-4 text-gray-500">or</span>
            <hr class="flex-grow border-gray-300">
          </div> -->
          <!-- <button  class="font-medium text-xl gap-5 w-full bg-white text-gray-700 py-2 border border-gray-300 rounded-lg hover:bg-gray-50 transition duration-200 flex items-center justify-center">
            <svg xmlns="http://www.w3.org/2000/svg" x="0px" y="0px" width="30" height="30" viewBox="0 0 48 48">
<path fill="#FFC107" d="M43.611,20.083H42V20H24v8h11.303c-1.649,4.657-6.08,8-11.303,8c-6.627,0-12-5.373-12-12c0-6.627,5.373-12,12-12c3.059,0,5.842,1.154,7.961,3.039l5.657-5.657C34.046,6.053,29.268,4,24,4C12.955,4,4,12.955,4,24c0,11.045,8.955,20,20,20c11.045,0,20-8.955,20-20C44,22.659,43.862,21.35,43.611,20.083z"></path><path fill="#FF3D00" d="M6.306,14.691l6.571,4.819C14.655,15.108,18.961,12,24,12c3.059,0,5.842,1.154,7.961,3.039l5.657-5.657C34.046,6.053,29.268,4,24,4C16.318,4,9.656,8.337,6.306,14.691z"></path><path fill="#4CAF50" d="M24,44c5.166,0,9.86-1.977,13.409-5.192l-6.19-5.238C29.211,35.091,26.715,36,24,36c-5.202,0-9.619-3.317-11.283-7.946l-6.522,5.025C9.505,39.556,16.227,44,24,44z"></path><path fill="#1976D2" d="M43.611,20.083H42V20H24v8h11.303c-0.792,2.237-2.231,4.166-4.087,5.571c0.001-0.001,0.002-0.001,0.003-0.002l6.19,5.238C36.971,39.205,44,34,44,24C44,22.659,43.862,21.35,43.611,20.083z"></path>
</svg>
            Sign in with Google
          </button> -->
      </form>
      <!-- <p class=" font-medium text-center text-gray-700 mt-4">Don't have an account? <a href="#" class="text-red-500 hover:underline">Sign up for free!</a></p> -->
      </div>
    </div>

  </div>
</template>
