<template>
  <li class="item">
    <input
      type="checkbox"
      class="item__checkbox"
      @change="$emit('onComplete', todo.id)"
    />
    <p
      class="item__content"
      :class="{ 'item__content--completed': todo.isCompleted }"
    >
      {{ todo.content }}
    </p>
    <Button type="button" name="삭제하기" @click="$emit('onDelete', todo.id)" />
  </li>
</template>

<script>
import Button from "./Button.vue";

export default {
  components: {
    Button,
  },
  props: {
    todo: Object,
  },
};
</script>

<style scoped>
.item {
  display: flex;
  width: 100%;
  height: 40px;
  margin-bottom: 10px;
}
.item:last-child {
  margin-bottom: 0;
}
.item__checkbox {
  width: 20px;
  height: 100%;
  margin-right: 5px;
}
.item__content {
  margin-right: 5px;
  line-height: 40px;
  border-bottom: 1px solid rgba(0, 0, 0, 0.11);
  flex: 1;
}
.item__content--completed {
  color: rgba(0, 0, 0, 0.3);
  text-decoration: line-through;
}
</style>
