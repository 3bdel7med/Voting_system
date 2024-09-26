<template>
  <form>
    <!-- 2 column grid layout with text inputs for the first and last names -->
    <div class="row mb-4">
      <div class="col">
        <div data-mdb-input-init class="form-outline">
          <input type="text" v-model="voite.first_name" id="form6Example1" class="form-control" />
          <label class="form-label" for="form6Example1">First name</label>
        </div>
      </div>
      <div class="col">
        <div data-mdb-input-init class="form-outline">
          <input type="text" v-model="voite.last_name" id="form6Example2" class="form-control" />
          <label class="form-label" for="form6Example2">Last name</label>
        </div>
      </div>
    </div>

    <!-- Text input -->
    <div data-mdb-input-init class="form-outline mb-4">
      <label class="form-label" for="form6Example3">Voite</label>
      <select class="form-select" v-model="voite.vote" aria-label="Default select example">
        <option selected>Open this select menu</option>
        <option value="1">One</option>
        <option value="2">Two</option>
        <option value="3">Three</option>
      </select>
    </div>

    <!-- Text input -->
    <div data-mdb-input-init class="form-outline mb-4">
      <input type="text" v-model="voite.address" id="form6Example4" class="form-control" />
      <label class="form-label" for="form6Example4">Address</label>
    </div>

    <!-- Email input -->
    <div data-mdb-input-init class="form-outline mb-4">
      <input type="email" v-model="voite.email" id="form6Example5" class="form-control" />
      <label class="form-label" for="form6Example5">Email</label>
    </div>

    <!-- Number input -->
    <div data-mdb-input-init class="form-outline mb-4">
      <input type="number" v-model="voite.phone" id="form6Example6" class="form-control" />
      <label class="form-label" for="form6Example6">Phone</label>
    </div>

   

   

    <!-- Submit button -->
    <button @click="submitForm" data-mdb-ripple-init type="button" class="btn btn-primary btn-block mb-4">Voite Now</button>
  </form>
</template>

<script>
import axios from 'axios';
import Swal from 'sweetalert2';
export default {
    
    data() {
        return {
            voite: {
                id: '',
                first_name: '',
                last_name: '',
                vote: '',
                address:'',
                email: '',
                phone:'',
            },
            message:[],
            'one':0,
            'tow':0,
        }

    },
  
    methods: {
       /* fetchPosts() {
            axios.get('/api/posts')
                .then(response => this.posts = response.data)
                .catch(error => console.log(error))
        },*/
        submitForm() {
            axios.post('http://127.0.0.1:8000/api/vote', this.voite).then(response => {
              this.message=response.data.data;
            })
            alert('success voiting');
            this.showAlert();
        },
        showAlert() {
            Swal.fire({
                icon: 'success',
                title: 'Success',
                text: 'Voite created successfully',
            });
        },
    }
}
</script>