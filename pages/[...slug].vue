<script setup>
const { path } = useRoute();

const { data } = await useAsyncData('page-data-' + path, () => {
  return queryContent().where({ _path: path }).findOne();
});
</script>

<template>
  <main>
    <ContentDoc v-slot="{ doc }">
      <ContentRenderer :value="data" :excerpt="false" />
    </ContentDoc>
  </main>
</template>
