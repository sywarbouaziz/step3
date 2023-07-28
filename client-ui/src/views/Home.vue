<template>
  <section>
    <div class="form-container">
      <form class="custom-form" @submit.prevent="submitForm">
        <div class="input-container">
          <input type="text" placeholder="Enter your location, please" v-model="location">
          <i class="custom-icon" @click="locatorButtonPressed">⚫</i>
        </div>
        <div class="error-message" v-if="errors.location">{{ errors.location }}</div>
        <button type="submit" class="custom-button">Let's go</button>
      </form>
    </div>
  </section>
</template>

<script lang="ts">
import { defineComponent, onMounted } from "vue";
import { resetPageBreadcrumbs } from "@/core/helpers/config";

export default defineComponent({
  name: "home",
  components: {},
  setup() {
    onMounted(async () => {
    resetPageBreadcrumbs();
    });
  },
  data() {
    return {
      location: "",
      errors: {
        location: "", // Error message for the location field
      },
    };
  },
  methods: {
    locatorButtonPressed() {
      // Implement the functionality for the locator button click event here
      alert("Locator button clicked!");
    },
    submitForm() {
      // Reset previous errors
      this.errors.location = "";

      // Perform form validation
      if (!this.location.trim()) {
        this.errors.location = "Please enter your location.";
        return;
      }

      // Form submission logic (add your code here)
      // Example: You can call an API, save data, etc.
      // For demonstration, we'll just show an alert with the location value.
      alert("Let's go button clicked! Location: " + this.location);

      // Clear the input field after form submission
      this.location = "";
    },
  },
});
</script>
<style>
/* Custom styles for the form */
.form-container {
  display: flex;
  justify-content: center;
}

.custom-form {
  width: 300px;
  border: 1px solid #ccc;
  padding: 10px;
  background-color: #f9f9f9;
}

.input-container {
  display: flex;
  align-items: center;
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 5px;
}

input {
  flex: 1;
  border: none;
  padding: 5px;
}

.custom-icon {
  cursor: pointer;
  margin-left: 5px;
}

.custom-button {
  display: block;
  width: 100%;
  margin-top: 10px;
  padding: 8px;
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.custom-button:hover {
  background-color: #0056b3;
}
</style>


















