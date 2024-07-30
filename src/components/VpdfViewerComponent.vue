<script setup lang="ts">
import { VPdfViewer, useLicense, ToolbarOptions } from '@vue-pdf-viewer/viewer';

const props = withDefaults(
  defineProps<{
    src: string;
    toolbarOptions?: Partial<ToolbarOptions> | false;
  }>(),
  {
    toolbarOptions: undefined,
  }
);
const licenseKey = import.meta.env.VITE_VPV_LICENSE ?? 'your-VPV-license-key';
useLicense({ licenseKey });
</script>

<template>
  <VPdfViewer v-bind="props" />
</template>
