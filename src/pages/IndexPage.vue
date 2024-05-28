<template>
  <q-page class="flex flex-center">
    <q-stepper
      v-model="activeStep"
      header-nav
      animated
    >
      <q-step title="Event Type" name="eventType">
        <q-page>
          <router-link to="/selectStudent">
          <img
            alt="Quasar logo"
            src="~assets/quasar-logo-vertical.svg"
            style="width: 200px; height: 200px"
          >
          </router-link>
          <!-- Add content for Step 1 -->
        </q-page>
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
import SelectStudent from './SelectStudent.vue'

defineOptions({
  name: 'IndexPage'
})
const activeStep = ref('eventType')
</script>
