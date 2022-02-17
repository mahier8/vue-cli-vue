<template>
  <h1>{{ title }}</h1>
  <input type="text" ref="name" />
  <button @click="handleClick">click me</button>
  <Modal />
</template>

<script>
import Modal from "./components/Modal.vue";

export default {
  name: "App", // name is optional
  components: {
    Modal,
  },
  data() {
    return {
      title: "My First Vue App",
    };
  },
  methods: {
    handleClick() {
      // accessing refs within the above input tag
      console.log(this.$refs.name);
      // to add a class, when we click on the button click me
      this.$refs.name.classList.add("active");
      // to focus on the input, when we click on the button click me
      this.$refs.name.focus();
    },
  },
};
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
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
