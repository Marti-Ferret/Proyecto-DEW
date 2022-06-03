<template>
  <div class="about">
    <CalendarioPage/>
  </div>
</template>

<script>
// @ is an alias to /src
import CalendarioPage from '@/components/CalendarioPage.vue'

export default {
  name: 'CalendarioPage',
  components: {
    CalendarioPage
  }
}
</script>