<template>
  <form @submit.prevent="onSubmit">
    <input v-model="title" type="text" placeholder="Add a todo" @input="onChange" />
    <button type="submit">Add</button>
  </form>
</template>

<script setup>
import { ref } from 'vue';
import { useTodoStore } from '@/stores/todoStore';

// 使用 pinia 的 todoStore
const todoStore = useTodoStore();

// 使用 ref 來儲存 title 的狀態
const title = ref('');

// 定義 onChange 方法來處理輸入框變更
const onChange = (e) => {
  title.value = e.target.value;
};

// onSubmit 方法處理表單提交
const onSubmit = () => {
  if (!title.value) {
    alert('Title is required');
    return;
  }

  // 使用 store 來新增 todo
  todoStore.addTodo({
    title: title.value,
    completed: false
  });

  console.log(title.value);

  // 重置輸入框
  title.value = '';
};
</script>
