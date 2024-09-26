<template>
    <div>
    <div class="bodybo">
        <div class="text-center fade-in">
            <h1>Welcome to the Voting System</h1>
            <p>Your voice matters! Participate in the upcoming vote.</p>
            <button style="color:red" class=" vote-button"><router-link to="/voite"> Vote Now</router-link> </button>
        </div>
        <CondidateComponent />
        
       
    </div>

    <Bar
    id="my-chart-id"
    :options="chartOptions"

    v-if="loaded" :data="chartData"
  />
    </div>
</template>
<style>

.carousel-item {
    background-color: #f8f9fa;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    margin: 0;
    text-align: center;
}
.candidate-image {
    border-radius: 50%;
    width: 150px;
    height: 150px;
    object-fit: cover;
}
        .bodybo {
            background-color: #f8f9fa;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
        }
        .vote-button {
            padding: 15px 30px;
            font-size: 20px;
            transition: transform 0.3s, background-color 0.3s;
            color: white;
        }
        .vote-button:hover {
            transform: scale(1.1);
            background-color: #04111f;
            color: white;
        }
        .fade-in {
            opacity: 0;
            animation: fadeIn 1s forwards;
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
    </style>
<script>
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

export default {
  name: 'BarChart',
  components: { Bar },
  data() {
    return {
      chartData: {
        labels: [ 'January', 'February', 'March' ],
        datasets: [ { data: [40, 20, 12] } ]
      },
      chartOptions: {
        responsive: true
      }
    }
  }
}

</script>