<template>
    <q-page class="flex flex-center">
    <h1>People List</h1>
    <div class="people-list">
      <div v-for="person in people" :key="person.name" class="person">
        <q-avatar rounded>
          <img :src="person.avatar" :alt="person.name" />
        </q-avatar>
        <p>{{ person.name }}</p>
      </div>
    </div>
    </q-page>
</template>

<script setup>
import { ref } from 'vue'

defineOptions({
  name: 'IndexPage'
})

const people = ref([
  { name: 'John Doe', avatar: 'john-doe.jpg' },
  { name: 'Jane Smith', avatar: 'jane-smith.jpg' },
  { name: 'Michael Johnson', avatar: 'michael-johnson.jpg' },
  { name: 'Emily Davis', avatar: 'emily-davis.jpg' },
  { name: 'William Brown', avatar: 'william-brown.jpg' },
  { name: 'Sophia Wilson', avatar: 'sophia-wilson.jpg' },
  { name: 'James Miller', avatar: 'james-miller.jpg' },
  { name: 'Isabella Martinez', avatar: 'isabella-martinez.jpg' },
  { name: 'Liam Anderson', avatar: 'liam-anderson.jpg' },
  { name: 'Olivia Taylor', avatar: 'olivia-taylor.jpg' }
])
</script>

<style scoped>
.people-list {
  display: flex;
  flex-wrap: wrap;
}
.person {
  flex: 1 0 20%; /* Each item takes up 20% of the row */
  box-sizing: border-box;
  padding: 10px;
  text-align: center;
}
.person img {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  object-fit: cover;
}
.person p {
  margin-top: 10px;
  font-size: 16px;
}
</style>
