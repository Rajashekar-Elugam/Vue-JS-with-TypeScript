<template>
  <div>
    <p>{{ myName }} - {{ age }}</p>
    <button @click="changeName('Srinivas')">Change Name</button>
    <button @click="changeAge(29)">Change Age</button>
    <!-- <button @click="changeName('Srinivas'), changeAge(29)">Change both</button> -->
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, toRefs } from "vue";

export default defineComponent({
  name: "App",

  data() {
    return {
      myName: "Rajashekar",
      age: 25 as number | string,
    };
  },

  setup() {
    const state = reactive({
      myName: "Rajashekar",
      age: 26 as number | string,
    });

    return {
      ...toRefs(state),
    };

    // const myName = ref("Rajashekar");
    // const age = ref<number | string>(28);

    // return { myName, age };
  },

  methods: {
    changeName(newName: string) {
      this.myName = newName;
    },

    changeAge(newAge: number) {
      this.age = newAge;
    },
  },
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
