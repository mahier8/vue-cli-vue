<template>
  <!-- by adding the .self to the click event, only
when we click on the backdrop, will the modal change -->
  <div class="backdrop" @click.self="closeModal">
    <div class="modal" :class="{ sale: theme === 'sale' }">
      <!-- we read from the data below in the props -->
      <!-- <h1>{{ header }}</h1> -->
      <!-- we can also use data binding, to add in an array -->
      <!-- <h1>{{ header }}</h1>
      <p>{{ text }}</p> -->

      <!-- slots, the data is passed from the App.js, then presented here -->
      <slot>default content</slot>
      <div class="actions">
        <slot name="links"></slot>
      </div>
    </div>
  </div>
</template>

<script>
// we take in data from props, and name the prop we want
export default {
  // props: ["header", "text", "theme"],
  props: ["theme"],

  methods: {
    closeModal() {
      // emitting custom events
      this.$emit("close");
    },
  },
};
</script>

<style scoped>
.modal {
  width: 400px;
  padding: 20px;
  margin: 100px auto;
  background: white;
  border-radius: 10px;
}

.backdrop {
  top: 0;
  position: fixed;
  background: rgba(0, 0, 0, 0.5);
  width: 100%;
  height: 100%;
}

h1 {
  color: aquamarine;
  border: none;
  padding: 0;
}

.modal p {
  font-style: normal;
}

.modal .actions {
  text-align: center;
  margin: 30px 0 10px 0;
  color: #333;
}

.modal .actions {
  color: #333;
  padding: 8px;
  border: 1px solid #eee;
  border-radius: 4px;
  text-decoration: none;
  margin: 10px;
}

.modal.sale {
  background: crimson;
  color: white;
}

.modal.sale.h1 {
  color: white;
}

.modal.sale.actions {
  color: white;
}

.modal.sale.actions a {
  color: white;
}
</style>
