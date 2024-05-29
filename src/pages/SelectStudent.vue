<template>
  <q-page @click="selectStudent(null)">
    <div class="students-grid">
      <div
        v-for="student in students"
        :key="student.name"
        class="student-item"
        @click="selectStudent(student, $event)"
        :class="{ selected: student === modelValue }"
      >
      <q-avatar rounded>
        <img :src="student.avatar" :alt="student.name" />
      </q-avatar>
      <p>{{ student.name }}</p>
      </div>
    </div>
  </q-page>
</template>

<script setup>
defineProps({
  students: Array,
  modelValue: Object
})

const emit = defineEmits(['update:modelValue'])

function selectStudent (student, event) {
  event?.stopPropagation()
  emit('update:modelValue', student)
}
</script>

<style scoped>
.students-grid {
  display: flex;
  flex-wrap: wrap;
}
.student-item {
  flex: 1 0 20%; /* Each item takes up 20% of the row */
  box-sizing: border-box;
  padding: 10px;
  text-align: center;
  cursor: pointer;
  transition: border 0.3s ease, background-color 0.3s ease; /* Smooth transition for visual changes */
}
.student-item img {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  object-fit: cover;
}
.student-item p {
  margin-top: 10px;
  font-size: 16px;
}
.student-item.selected {
  outline: 2px solid blue; /* Highlight the selected student */
  background-color: rgba(0, 0, 255, 0.1); /* Light blue background to indicate selection */
}
</style>
