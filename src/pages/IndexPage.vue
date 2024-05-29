<template>
  <q-page class="flex flex-center">
    <q-stepper
      v-model="activeStep"
      ref="stepper"
      header-nav
      animated
    >
      <q-step title="Gestion / Prevention" name="gestionPrevention">
        <gestion-prevention />
      </q-step>
      <q-step title="Select Student" name="selectStudent">
        <select-student />
      </q-step>
      <q-step title="Select Teacher" name="selectTeacher">
        <q-page>
          <h2>Step 3 Content</h2>
          <!-- Add content for Step 3 -->
        </q-page>
      </q-step>
    </q-stepper>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'
import GestionPrevention from './GestionPrevention.vue'
import SelectStudent from './SelectStudent.vue'

defineOptions({
  name: 'IndexPage'
})

const activeStep = ref('gestionPrevention')
</script>
