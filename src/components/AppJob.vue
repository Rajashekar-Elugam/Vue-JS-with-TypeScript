<template>
  <div>
    <header>
      <h1 class="title">My Job Portal</h1>
      <div class="">
        <button @click="handleClick('title')">Order by Title</button>
        <button @click="handleClick('location')">Order by Location</button>
        <button @click="handleClick('salary')">Order by Salary</button>
      </div>
    </header>
    <JobsList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";

import Job from "../types/Job";
import JobsList from "./JobsList.vue";
import OrderTerm from "../types/OrderTerm";

export default defineComponent({
  name: "AppJob",
  components: {
    JobsList,
  },
  setup() {
    const jobs = ref<Job[]>([
      { title: "farm worker", location: "Hyderabad", salary: 25000, id: "1" },
      { title: "quarryman", location: "Bengalore", salary: 40000, id: "2" },
      { title: "flute player", location: "Chennai", salary: 35000, id: "3" },
      { title: "fisherman", location: "Pune", salary: 21000, id: "4" },
      { title: "prison guard", location: "Mumbai", salary: 32000, id: "5" },
    ]);

    const order = ref<OrderTerm>("title");
    const handleClick = (term: OrderTerm) => {
      order.value = term;
    };

    return { jobs, handleClick, order };
  },
});
</script>

<style>
header {
  text-align: center;
}
header.order {
  margin-top: 20px;
}
button {
  margin: 0 10px;
  color: #1195c9;
  border: 3px solid #1195c9;
  background: #d5f0ff;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
.title {
  color: yellow;
  font-size: 30px;
}
</style>
