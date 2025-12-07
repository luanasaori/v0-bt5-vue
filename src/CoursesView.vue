<script setup lang="ts">
import { computed } from "vue";
import { useI18n } from "vue-i18n";
import SpecsCardGrid from '@/components/specsCard/SpecsCardGrid.vue';

const { t, locale } = useI18n();


const dataUrl = computed(() => {
  const mapping: Record<string, string> = {
    pt: '/src/data/courses_pt.json',
    en: '/src/data/courses_en.json',
    es: '/src/data/courses_es.json',
    fr: '/src/data/courses_fr.json'
  };
  
  return mapping[locale.value] || mapping.pt;
});
</script>

<template>
  <div class="container mt-5">
    <h1>{{ t("coursesPage.title") }}</h1>
    
    <SpecsCardGrid 
      :key="locale"
      :apiURL="dataUrl" 
      titleKey="nome" 
      subTitleKey="duracao"
      descriptionKey="objetivo"
    />
  </div>
</template>
