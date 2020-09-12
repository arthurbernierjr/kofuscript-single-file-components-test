<template>
  <div class="container">
    <ComingSoonSplash />
  </div>
</template>

<script>
import component from '@/scripts/controllers/index.kofu'
import ComingSoonSplash from '@/scripts/components/ComingSoonSplash'
export default {
  ...component,
  ...{
    components:
    {
      ComingSoonSplash
    }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
</style>
