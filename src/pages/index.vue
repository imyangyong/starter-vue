<script setup lang="ts">
defineOptions({
  name: 'IndexPage',
})
const _user = useUserStore()

const { t } = useI18n()
</script>

<template>
  <div>
    <h2>
      {{ t('title') }}
    </h2>
  </div>
</template>

<route lang="yaml">
meta:
  layout: home
</route>
