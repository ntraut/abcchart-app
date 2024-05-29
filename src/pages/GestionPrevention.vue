<template>

  <div class="q-pa-md q-gutter-md">
    <q-btn color="deep-orange" @click="selectRoomPurpose(true)" label="Gestion" />
    <q-btn color="light-green" @click="selectRoomPurpose(false)" label="Prevention" />
  </div>

</template>

<script setup>
const props = defineProps({
  stepper: Object
})

function selectRoomPurpose (isGestion) {
  console.log(isGestion) // TD: keep track of the flag isGestion
  props.stepper.next()
}
</script>
