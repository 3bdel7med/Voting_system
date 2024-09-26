

<template>
  

<div class="container my-4">
<div class="row">
    <div class="col-md-3 candidate-card">
        <div class="card">
            <img src="../assets/download (3).png" class="card-img-top" alt="Candidate 1">
            <div class="card-body">
                <h5 class="card-title">Candidate 1</h5>
                <p>Votes: <span class="votes">1200</span></p>
                <div class="mini-chart" data-votes="1200" style="width: 100%;"></div>
                <p>Party: Democratic</p>
                <p>Age: 45</p>
            </div>
        </div>
    </div>
    <div class="col-md-3 candidate-card">
        <div class="card">
            <img src="../assets/download.png" class="card-img-top" alt="Candidate 2">
            <div class="card-body">
                <h5 class="card-title">Candidate 2</h5>
                <p>Votes: <span class="votes">900</span></p>
                <div class="mini-chart" data-votes="900" style="width: 75%;"></div>
                <p>Party: Republican</p>
                <p>Age: 50</p>
            </div>
        </div>
    </div>
    <div class="col-md-3 candidate-card">
        <div class="card">
            <img src="../assets/download (2).png" class="card-img-top" alt="Candidate 3">
            <div class="card-body">
                <h5 class="card-title">Candidate 3</h5>
                <p>Votes: <span class="votes">750</span></p>
                <div class="mini-chart" data-votes="750" style="width: 62.5%;"></div>
                <p>Party: Independent</p>
                <p>Age: 38</p>
            </div>
        </div>
    </div>
    <div class="col-md-3 candidate-card">
        <div class="card">
            <img src="../assets/download (1).png" class="card-img-top" alt="Candidate 4">
            <div class="card-body">
                <h5 class="card-title">Candidate 4</h5>
                <p>Votes: <span class="votes">600</span></p>
                <div class="mini-chart" data-votes="600" style="width: 50%;"></div>
                <p>Party: Green</p>
                <p>Age: 42</p>
            </div>
        </div>
    </div>
</div>
</div>
</template>
<script>
// JavaScript to calculate mini-chart widths
const maxVotes = 1200; // Adjust this to the maximum votes among candidates
document.querySelectorAll('.mini-chart').forEach(chart => {
    const votes = parseInt(chart.getAttribute('data-votes'));
    const chartWidth = (votes / maxVotes) * 100;
    chart.style.width = chartWidth + '%';
});
</script>
<style>
.mini-chart {
    background: #007bff;
    border-radius: 5px;
    height: 20px;
    transition: width 0.3s ease;
}
.candidate-card {
    margin-bottom: 20px;
}
</style>