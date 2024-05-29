<template>
  <q-page class="flex flex-center">
    <q-stepper
      v-model="activeStep"
      ref="stepper"
      header-nav
      animated
    >
      <q-step title="Gestion / Prevention" name="gestionPrevention">
        <gestion-prevention :stepper="$refs.stepper"/>
      </q-step>
      <q-step title="Student" name="selectStudent">
        <select-student :students="students" v-model:modelValue="selectedStudent" :stepper="$refs.stepper" />
      </q-step>
      <q-step title="Teacher" name="selectTeacher">
        <select-teacher :teachers="teachers" v-model:modelValue="selectedTeacher" />
      </q-step>
    </q-stepper>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'
import GestionPrevention from './GestionPrevention.vue'
import SelectStudent from './SelectStudent.vue'
import SelectTeacher from './SelectTeacher.vue'

defineOptions({
  name: 'IndexPage'
})

const activeStep = ref(null)
const selectedStudent = ref(null) // Initially, no student is selected
const selectedTeacher = ref(null) // Initially, no student is selected

function hashStringToNumber (str) {
  let hash = 5381
  for (let i = 0; i < str.length; i++) {
    hash = (hash * 33) ^ str.charCodeAt(i)
  }
  return hash >>> 0 // Ensure positive integer
}

function getRandomImage (name) {
  const seed = hashStringToNumber(name)
  // Use a random image service like Lorem Picsum, seeded with the hash value
  return `https://picsum.photos/seed/${seed}/100/100`
}

const studentNames = [
  'Élise Dubois',
  'Antoine Martin',
  'Camille Lambert',
  'Lucas Lefèvre',
  'Manon Girard',
  'Théo Moreau',
  'Charlotte Leroy',
  'Maxime Roux',
  'Juliette Renault',
  'Gabriel Bernard'
]

const students = ref(studentNames.map(teacher => ({
  name: teacher,
  avatar: getRandomImage(teacher)
})))

const teacherNames = [
  'Marie Dupont',
  'Jean Leclerc',
  'Sophie Rousseau',
  'Pierre Lambert',
  'Claire Lefèvre',
  'Michel Girard',
  'Alice Moreau',
  'Luc Leroy',
  'Anne Roussel',
  'Philippe Bernard'
]

const teachers = ref(teacherNames.map(teacher => ({
  name: teacher,
  avatar: getRandomImage(teacher)
})))
</script>
