<template>
  <button class="btn" :type="type" @click="$emit('delete')">{{ name }}</button>
</template>

<script>
export default {
  name: "Button",
  props: {
    type: String,
    name: String,
  },
};
</script>

<style>
.btn {
  background-color: transparent;
  border: 1px solid rgba(0, 0, 0, 0.6);
  border-radius: 3px;
}
.btn:hover {
  cursor: pointer;
}
</style>
