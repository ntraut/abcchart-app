<template>
  <q-page @click="selectTeacher(null)">
    <div class="teachers-grid">
      <div
        v-for="teacher in teachers"
        :key="teacher.name"
        class="teacher-item"
        @click="selectTeacher(teacher, $event)"
        :class="{ selected: teacher === modelValue }"
      >
        <q-avatar rounded>
          <img :src="teacher.avatar" :alt="teacher.name" />
        </q-avatar>
        <p>{{ teacher.name }}</p>
      </div>
    </div>
  </q-page>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue'

defineProps({
  teachers: Array,
  modelValue: Object
})

const emit = defineEmits(['update:modelValue'])

function selectTeacher (teacher, event) {
  event?.stopPropagation()
  emit('update:modelValue', teacher)
}
</script>

<style scoped>
.teachers-grid {
  display: flex;
  flex-wrap: wrap;
}
.teacher-item {
  flex: 1 0 20%; /* Each item takes up 20% of the row */
  box-sizing: border-box;
  padding: 10px;
  text-align: center;
  cursor: pointer;
  transition: outline 0.3s ease, background-color 0.3s ease; /* Smooth transition for visual changes */
}
.teacher-item img {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  object-fit: cover;
}
.teacher-item p {
  margin-top: 10px;
  font-size: 16px;
}
.teacher-item.selected {
  outline: 2px solid blue; /* Use outline instead of border to avoid layout shift */
  background-color: rgba(0, 0, 255, 0.1); /* Light blue background to indicate selection */
}
</style>
