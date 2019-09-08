<template>
  <v-layout
    justify-center
    align-center
  >
    <v-flex
      xs12
      sm8
      md6
    >
      <div class="text-xs-center">
        <fibbler />
      </div>
    </v-flex>
  </v-layout>
</template>

<script>
import Fibbler from '~/components/Fibbler.vue'

export default {
  components: {
    Fibbler
  }
}
</script>
