<script setup>
 import SingleJob from './SingleJob.vue';
 import jobData from '@/jobs2.json'
 import { ref, defineProps } from 'vue';

 defineProps({
    limit: Number,
    showButton: {
        type: Boolean,
        default: false
    }
 })

 const jobs =ref(jobData);
 console.log(jobs.value);
</script>

<template>
    <section class="bg-blue-100 px-5 py-9">
    <div class="container-xl lg:container m-auto">
    <h2 class="text-3xl font-bold text-green-600 mb-6 text-center">Browse Suitable Jobs</h2>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
     <SingleJob v-for="job in jobs.slice(0, limit || jobs.length)" :key="job.id" :job="job"/>
    </div>
    </div>
    </section>
    <section v-if="showButton" class="m-auto max-w-lg my-10 px-6">
      <a
        href="/jobs"
        class="block bg-black text-white text-center py-4 px-6 rounded-xl hover:bg-gray-700"
        >View All Jobs</a
      >
    </section>
</template>