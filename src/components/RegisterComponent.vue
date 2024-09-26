<template>
    <div class="text-2xl text-center">
    Join Us today
    </div>
    <div class="mt-2 mb-2 text-xl text-center">
    this is Sign Up Page
    </div>
    <div v-if="showSuccessMessage " class="text-green-600 text-center mt-4">
    Registration successful. Please login.
    </div>
    <div v-if="showErrorMessage " class="text-red-600 text-center mt-4">
    {{ errorMessage }}
    </div>
    <div class="p-5 m-5">
    <form @submit.prevent="validateAndRegister">
    <div class="mb-3 pt-0 text-center">
    <label class="block uppercase text-blueGray-600 text-xs font-bold mb-2" for="name">Name:</label>
    <input type="text" placeholder="Name"
    id="name"
    v-model="form.name"
    :class="{ 'border-red-500': showErrorName }"
    class="px-2 py-1 placeholder-blueGray-300 text-blueGray-600 relative
    bg-white rounded text-sm border border-blueGray-300 outline-none focus:outline-none focus:ring w-1/2 required"/>
    <div v-if="showErrorName" class="text-red-600 text-sm mt-1">Name is required</div>
    </div>
    <div class="mb-3 pt-0 text-center">
    <label class="block uppercase text-blueGray-600 text-xs font-bold mb-2" for="email">Email:</label>
    <input type="email"
    id="email"
    v-model="form.email"
    :class="{ 'border-red-500': showErrorEmail }"
    placeholder="Email"
    class="px-2 py-1 placeholder-blueGray-300 text-blueGray-600 relative
    bg-white rounded text-sm border border-blueGray-300 outline-none focus:outline-none focus:ring w-1/2 required"/>
    <div v-if="showErrorEmail" class="text-red-600 text-sm mt-1">Email is required</div>
    </div>
    <div class="mb-3 pt-0 text-center">
    <label class="block uppercase text-blueGray-600 text-xs font-bold mb-2" for="profile-picture">Profile Picture:</label>
    <input type="file"
    id="profile-picture"
    ref="profilePicture"
    class="w-1/2"
    @change="handleFileChange"
    accept="image/*">
    </div>
    <div class="mb-3 pt-0 text-center mx-auto">
    <img v-if="previewImage" :src="previewImage" class="w-1/4 h-2/4 mx-auto " alt="Profile Picture">
    </div>
    <div class="mb-3 pt-0 text-center">
    <label class="block uppercase text-blueGray-600 text-xs font-bold mb-2" for="password">Password:</label>
    <input v-model="form.password"
    :class="{ 'border-red-500': showErrorPassword }"
    type="password"
    id="password"
    placeholder="Password"
    class="px-2 py-1 placeholder-blueGray-300 text-blueGray-600 relative
    bg-white rounded text-sm border border-blueGray-300 outline-none focus:outline-none focus:ring w-1/2 required"/>
    <div v-if="showErrorPassword" class="text-red-600 text-sm mt-1">Password is required</div>
    </div>
    <div class="mb-2 pt-0 text-center">
    <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
    Sign Up
    </button>
    </div>
    </form>
    </div>
    </template>
    <script setup>
    import { ref } from 'vue';
    import axios from 'axios';
    // Define refs for form fields
    const showSuccessMessage = ref(false);
    const showErrorMessage = ref(false);
    const errorMessage = ref('');
    const showErrorName = ref(false);
    const showErrorEmail = ref(false);
    const showErrorPassword = ref(false);
    const previewImage = ref('');
    const form = ref({
    name: '',
    email: '',
    password: '',
    profile_picture: '',
    });
    const resetForm = () => {
    form.value = {
    name: '',
    email: '',
    password: '',
    profile_picture: '',
    };
    previewImage.value = '';
    // Clear the file input element
    const fileInput = document.getElementById('profile-picture');
    if (fileInput) {
    fileInput.value = null;
    }
    }
    const handleFileChange = (event) => {
    form.value.profile_picture = event.target.files[0];
    const reader = new FileReader();
    reader.readAsDataURL(form.value.profile_picture);
    reader.onload = (e) => {
    previewImage.value = e.target.result;
    };
    }
   // const handleValidation = () => {
     // showErrorName.value = !name.value;
    // showErrorEmail.value = !email.value;
    // showErrorPassword.value = !password.value;
    // profile_picture.value = !profilePicture.value;
    // if (showErrorName.value || showErrorEmail.value || showErrorPassword.value) {
    // return false;
    // }
    // return true;
    //}
    const validateAndRegister = async () => {
    try {
    // if (!handleValidation()) {
    // return;
    // }
    const formData = new FormData();
    for (const key in form.value) {
    formData.append(key, form.value[key]);
    }
    const response = await axios.post('/api/users', formData, {
    headers: {
    'Content-Type': 'multipart/form-data',
    },
    });
    if (response.status) {
    console.log('here');
    showSuccessMessage.value = true;
    showErrorMessage.value = false;
    resetForm();
    } else {
    console.error('Unexpected response status:', response.status);
    }
    } catch (error) {
    if (error.isAxiosError && error.response) {
    console.error('Server validation errors:', error.response.data);
    errorMessage.value = error.response.data.message;
    } else {
    console.error('An error occurred:', error);
    errorMessage.value = 'An error occurred while processing your request.';
    }
    showSuccessMessage.value = false;
    showErrorMessage.value = true;
    }
    }
    </script>