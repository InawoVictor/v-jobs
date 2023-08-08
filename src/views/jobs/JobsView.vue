<template>
    <h1>Jobs</h1>
    <div v-if="jobs.length">
        <div v-for="job in jobs" :key="job.id" class="job">
            <h2>
                <router-link :to="{name: 'JobDetails', params: {id: job.id}}">
                    {{job.title}}
                </router-link>
            </h2>
        </div>
    </div>
    <div v-else>Loading job...</div>
</template>
                

<script>
export default {
    name: "JobsView",
    data() { 
        return {
            jobs: []  
        }
    },
    mounted() {
        fetch("http://localhost:3000/jobs")
        .then((res) => res.json())
        .then(data => this.jobs = data)
        .catch(err => console.log(err.message))
    }
} 
</script>

<style>
    .job h2 {
        background: #f4f4f4;
        padding: 20px;
        border-radius: 10px;
        margin: 10px auto;
        max-width: 600px;
        cursor: pointer;
        color: #444;
        transition: all .3s;
    }
    .job h2:hover{
        background: #ddd;
    }
    .job a {
        text-decoration: none;
        color: #444;
    }
</style>