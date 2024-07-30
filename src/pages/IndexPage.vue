<script setup lang="ts">
import { VPdfViewer, useLicense } from '@vue-pdf-viewer/viewer';

const licenseKey = import.meta.env.VITE_VPV_LICENSE ?? 'your-VPV-license-key';
useLicense({ licenseKey });
const pdfFileSource =
  'https://raw.githubusercontent.com/mozilla/pdf.js/ba2edeae/web/compressed.tracemonkey-pldi-09.pdf';
</script>
<template>
  <div :style="{ width: '1028px', height: '700px' }">
    <VPdfViewer :src="pdfFileSource" />
  </div>
</template>
