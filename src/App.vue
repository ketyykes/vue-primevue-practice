<script setup>
import { useRouter } from 'vue-router';
import { ref } from 'vue';
import Menubar from 'primevue/menubar';

const router = useRouter();

const items = ref([
  {
    label: 'Home',
    icon: 'pi pi-home',
    command: () => {
      router.push('/');
    }
  },
  {
    label: 'About',
    icon: 'pi pi-info-circle',
    command: () => {
      router.push('/about');
    }
  }
]);
</script>

<template>
  <header>
    <div>
      <nav>
        <Menubar :model="items" />
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
nav {
  margin-bottom: 20px;
}
</style>
