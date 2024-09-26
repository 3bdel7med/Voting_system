<template>
  <div class="row">
    <div class="col-1"></div>
    <div class="col-10" >
      <div class="row">
        <form class="row">
          <div class="form-group col-6">
            <label for="name">First Name:</label>
            <input type="text" class="form-control" id="first_name" placeholder="Enter first_name" v-model="users.first_name" required>
          </div>
          <div class="form-group col-6">
            <label for="last_name">Last Name:</label>
            <input type="text" class="form-control" id="last_name" placeholder="Enter last_name" v-model="users.last_name" required>
          </div>
          <div class="form-group col-6">
            <label for="email">Email:</label>
            <input type="email" class="form-control" id="email" placeholder="Enter email" v-model="users.email" required>
          </div>
          <div class="form-group col-6">
            <label for="password">Password:</label>
            <input type="password" class="form-control" id="password" placeholder="Enter password" v-model="users.password" required>
          </div>
          <div class="form-group col-6">
            <label for="phone">Phone:</label>
            <input type="tel" class="form-control" id="phone" placeholder="Enter phone" v-model="users.phone" required>
          </div>

          <div class="form-group col-6">
            <label for="address">Address:</label>
            <input type="address" class="form-control" id="address" placeholder="Enter address" v-model="users.address" required>
          </div>
          
          <button type="submit" class="btn btn-primary" @click="submitForm()">Submit</button>
        </form>
      </div>
    </div>
    <div class="col-1"></div>
  </div>
</template>

<script>
import axios from 'axios';
import Swal from 'sweetalert2';
export default {
    
    data() {
        return {
            users: {
                id: '',
                first_name: '',
                last_name: '',
                password: '',
                address:'',
                email: '',
                phone:'',
            },
            message:[],
            
        }

    },
  
    methods: {
    
        submitForm() {
            axios.post('http://127.0.0.1:8000/api/user', this.user).then(response => {
              this.message=response.data.data;
            })
            alert('success voiting');
            this.showAlert();
        },
        showAlert() {
            Swal.fire({
                icon: 'success',
                title: 'Success',
                text: 'user created successfully',
            });
        },
    }
}
</script>