<template>
  <div>
    <DataTable :value="todos" responsiveLayout="scroll">
      <Column field="title" header="待辦事項"></Column>
      <Column field="completed" header="已完成"></Column>
      <Column header="操作">
        <template #body="slotProps">
          <Button @click="removeTodo(slotProps.rowIndex)" icon="pi pi-trash" />
        </template>
      </Column>
    </DataTable>
  </div>
</template>

<script setup>
import { useTodoStore } from '../stores/todoStore';
import Button from 'primevue/button';
import Column from 'primevue/column';
import DataTable from 'primevue/datatable';

const todoStore = useTodoStore();
const todos = todoStore.todos;

console.log(todos);

const removeTodo = (index) => {
  todoStore.removeTodo(index);
};
</script>

<style scoped></style>
