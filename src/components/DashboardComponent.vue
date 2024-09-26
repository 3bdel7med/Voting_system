<template>
    <div>
        <div class="container">
            <div class="row justify-content-center">
                <div class="col-md-10">
                    <div class="card">
                        <div class="card-header">Dashboard</div>
                        <div class="card-body" v-for="vote in vote" :key="vote">

                            <div class="alert alert-success" role="alert">

                            </div>

                            <div class="container">
                                
                                <div class="row">
                                    <div class="col-sm">
                                        <router-link to="/first">
                                        <div class="card text-white bg-primary mb-3" style="max-width:
18rem;">
                                            <div class="card-header">First</div>
                                            <div class="card-body">
                                                <h5 class="card-title">{{ vote[0] }}</h5>
                                                
                                            </div>
                                        </div>
                                    </router-link>
                                    </div>
                                    <div class="col-sm">
                                        <router-link to="/second">
                                        <div class="card text-white bg-secondary mb-3" style="max-width:
18rem;">
                                            <div class="card-header">Thecond</div>
                                            <div class="card-body">
                                                <h5 class="card-title">{{ vote[1] }}</h5>
                                            </div>
                                        </div>
                                    </router-link>
                                    </div>
                                    <div class="col-sm">
                                        <router-link to="/third">
                                        <div class="card text-white bg-success mb-3" style="max-width:
18rem;">
                                            <div class="card-header">Third</div>
                                            <div class="card-body">
                                                <h5 class="card-title"> {{vote[2]}}</h5>
                                            </div>
                                        </div>
                                    </router-link>
                                    </div>
                                </div>
                            
                            </div>
                            <div class="container">
                            
                            
                            
                            
                            <router-link to='/forth'>
                                <div class="row">
                                    <div class="col-sm">
                                        <div class="card text-white bg-dark mb-3" style="max-width: 18rem;">
                                            <div class="card-header"><router-link to="/forth">  Forth</router-link></div>
                                            <div class="card-body">
                                                <h5 class="card-title">{{ vote[3] }}</h5>
                                    
                                            </div>
                                        </div>
                                    </div>
                                    
                                  
                                </div>
                            </router-link>
                            </div>
                            
                           
                        </div>
                    </div>
                </div>
            </div>
            
        </div>
        <div class="container">
            <table class="table">
                <thead>
                  <tr>
                    <th scope="col">#</th>
                    <th scope="col">First</th>
                    <th scope="col">Last</th>
                    <th scope="col">Handle</th>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <th scope="row">1</th>
                    <td>Mark</td>
                    <td>Otto</td>
                    <td>@mdo</td>
                  </tr>
                  <tr>
                    <th scope="row">2</th>
                    <td>Jacob</td>
                    <td>Thornton</td>
                    <td>@fat</td>
                  </tr>
                  <tr>
                    <th scope="row">3</th>
                    <td colspan="2">Larry the Bird</td>
                    <td>@twitter</td>
                  </tr>
                </tbody>
              </table>
        </div>
    </div>
</template>
<script>
import axios from 'axios';
export default {
    data() {
        return {
           vote:[]
        }
    },
    mounted() {
        this.feachData()
    },
    methods: {
        async feachData() {
            axios.get('http://127.0.0.1:8000/api/vote')
                .then(response => this.vote = response.data
              
                )
                .catch(error => console.log(error))
     
            
        }
    }
}
</script>