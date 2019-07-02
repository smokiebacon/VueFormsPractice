<template>
  <div>
    <p>Server Status: {{ status }}</p>
    <hr />
    <button class="button-primary" @click.prevent="changeStatus">Change Status</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      status: "Critical"
    };
  },
  methods: {
    changeStatus() {
      this.status = "Normal";
    }
  }
};
</script>

