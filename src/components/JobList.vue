<template>
  <div class="job-list">
    <p>Ordered by {{ order }}</p>
    <ul>
      <li v-for="job in orderdJobs" :key="job.id">
        <h2>{{ job.title }} in {{ job.location }}</h2>
        <div class="calary">
          <p>{{ job.salary }} rupees</p>
        </div>
        <div class="description">
          <p>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quo rem,
            aspernatur atque in iste laudantium. Culpa dolores reiciendis
            nesciunt, facilis eos officia unde deleniti ex eum. Voluptatem quas
            accusamus nostrum?
          </p>
        </div>
      </li>
    </ul>
  </div>
</template>
<script lang="ts">
import { computed, defineComponent, PropType } from "vue";
import Job from "../types/Job";
import OrderTerm from "../types/OrderTerm";
export default defineComponent({
  props: {
    jobs: {
      required: true,
      type: Array as PropType<Job[]>,
    },
    order: {
      required: true,
      type: String as PropType<OrderTerm>,
    },
  },
  setup(props) {
    const orderdJobs = computed(() => {
      return [...props.jobs].sort((a: Job, b: Job) => {
        return a[props.order] > b[props.order] ? 1 : -1;
      });
    });
    return { orderdJobs };
  },
});
</script>
<style lang="scss" scoped></style>
