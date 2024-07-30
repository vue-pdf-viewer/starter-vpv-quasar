<script setup lang="ts">
import VpdfViewerComponent from '../components/VpdfViewerComponent.vue';
import { ToolbarOptions } from '@vue-pdf-viewer/viewer';

const pdfFileSource =
  'https://raw.githubusercontent.com/mozilla/pdf.js/ba2edeae/web/compressed.tracemonkey-pldi-09.pdf';

const toolbarOptions: Partial<ToolbarOptions> | false = false;
</script>
<template>
  <div>
    <h1>VPV Starter Toolkit: Quasar + TypeScript</h1>
    <br />
    <h2>Default Toolbar</h2>
    <div>
      <div class="pdf-viewer-wrapper">
        <VpdfViewerComponent :src="pdfFileSource" />
      </div>
    </div>
    <h2>Without Toolbar</h2>
    <div>
      <div class="pdf-viewer-wrapper no-toolbar">
        <VpdfViewerComponent
          :src="pdfFileSource"
          :toolbar-options="toolbarOptions"
        />
      </div>
    </div>
    <h2>Mobile</h2>
    <div>
      <div class="pdf-viewer-wrapper-mobile">
        <VpdfViewerComponent :src="pdfFileSource" />
      </div>
    </div>
  </div>
</template>

<style scoped>
.pdf-viewer-wrapper {
  width: 1028px;
  height: 700px;
  margin: 0 auto;
}

.pdf-viewer-wrapper-mobile {
  width: 468px;
  height: 700px;
  margin: 0 auto;
}
.no-toolbar :deep(.vpv-variables) {
  --vpv-toolbar-size: 0px;
}
</style>
