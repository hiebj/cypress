<template>
  <div
    class="h-full grid gap-8px grid-cols-[16px,auto,auto] items-center"
    data-cy="spec-item"
  >
    <i-cy-document-blank_x16
      class="icon-light-gray-50 icon-dark-gray-200 group-hocus:icon-light-indigo-200 group-hocus:icon-dark-indigo-400"
    />

    <div
      :title="fileName + extension"
      class="text-gray-400 text-indigo-500 truncate group-hocus:text-indigo-600"
    >
      <HighlightedText
        :text="fileName"
        :indexes="indexes.filter((idx) => idx < fileName.length)"
        class="font-medium text-indigo-500 group-hocus:text-indigo-700"
        highlight-classes="text-gray-1000"
      />
      <HighlightedText
        :text="extension"
        :indexes="indexes.filter((idx) => idx >= fileName.length).map(idx => idx - fileName.length)"
        class="font-light group-hocus:text-gray-400"
        highlight-classes="text-gray-1000"
      />
      <slot />
    </div>
  </div>
</template>

<script lang="ts" setup>
import HighlightedText from './HighlightedText.vue'

withDefaults(defineProps<{
  fileName: string
  extension: string
  indexes?: number[]
}>(), { indexes: () => [] })
</script>
