<template>
  <div class="app">
    <button @click="handleClick('title')">order by title</button>
    <button @click="handleClick('salary')">order by salary</button>
    <button @click="handleClick('location')">order by location</button>
    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, ref, toRefs } from "vue";
import Job from "./types/Job";
import OrderTerm from "./types/OrderTerm";
import JobList from "./components/JobList.vue";
export default defineComponent({
  name: "App",
  components: { JobList },
  setup() {
    const jobs = ref<Job[]>([
      {
        title: "one",
        location: "location one",
        salary: 30000,
        id: "1",
      },
      {
        title: "two",
        location: "location two",
        salary: 30001,
        id: "2",
      },
      {
        title: "three",
        location: "location three",
        salary: 30003,
        id: "3",
      },
      {
        title: "four",
        location: "location four",
        salary: 30004,
        id: "4",
      },
      {
        title: "five",
        location: "location five",
        salary: 30005,
        id: "5",
      },
    ]);
    const order = ref<OrderTerm>("title");
    const handleClick = (term: OrderTerm) => {
      order.value = term;
    };
    return { jobs, handleClick, order };
  },
});
</script>

<style></style>
