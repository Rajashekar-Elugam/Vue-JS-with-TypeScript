<template>
  <div class="job-list">
    <p>
      Ordered by: <span>{{ order }}</span>
    </p>
    <transition-group name="list" tag="ul">
      <li v-for="job in orderedJobs" :key="job.id">
        <h2>{{ job.title }} in {{ job.location }}</h2>
        <div class="salary">
          <p>Rs. {{ job.salary }}</p>
        </div>
        <div class="description">
          <p>
            Lorem ipsum dolor, sit amet consectetur adipisicing elit. Officia reprehenderit expedita accusamus nisi doloremque, unde voluptatem. Non ratione est animi ipsam atque voluptatibus culpa
            libero nobis ut, magnam eligendi amet.
          </p>
        </div>
      </li>
    </transition-group>
  </div>
</template>

<script lang="ts">
import { computed, defineComponent, PropType } from "vue";

import Job from "@/types/Job";
import OrderTerm from "@/types/OrderTerm";

export default defineComponent({
  name: "JobsList",
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
    const orderedJobs = computed(() => {
      return [...props.jobs].sort((a: Job, b: Job) => {
        return a[props.order] > b[props.order] ? 1 : -1;
      });
    });

    return {
      orderedJobs,
    };
  },
});
</script>

<style scoped>
.job-list {
  max-width: 960px;
  margin: 40px auto;
}
span {
  color: yellow;
  font-weight: bold;
  text-decoration: underline;
}
.job-list ul {
  padding: 0;
}
.job-list li {
  list-style-type: none;
  background: lightgoldenrodyellow;
  padding: 16px;
  margin: 16px 0;
  border-radius: 4px;
}
.job-list h2 {
  margin: 0 0 10px;
  text-transform: capitalize;
}
.salary {
  display: flex;
}
.salary p {
  color: #17bf66;
  font-weight: bold;
  margin: 10px 4px;
}
.list-move {
  transition: all 0.75s;
}
</style>
