<script setup lang="ts">
  import VPdfAnnotation from '@vue-pdf-viewer/annotation';
  import { type ToolbarOptions, VPdfViewer, VPVBaseProps } from '@vue-pdf-viewer/viewer';
  import pdfWorker from 'pdfjs-dist/build/pdf.worker?url';
  import { computed, type PropType } from 'vue';

  const props = defineProps({
    ...VPVBaseProps,
    toolbarOptions: {
      type: [Object, Boolean] as PropType<Partial<ToolbarOptions> | false | null>,
      required: false,
      default: null,
    },
    annotateEnabled: {
      type: Boolean,
      required: false,
      default: false,
    },
  } as const);

  const vpvProps = computed(() => {
    // Destructure to exclude annotateEnabled from props
    const { annotateEnabled, ...baseProps } = props;

    // Create the final props object with worker URL and conditional plugins
    return {
      ...baseProps,
      workerUrl: pdfWorker,
      ...(annotateEnabled && { plugins: [VPdfAnnotation()] }),
    };
  });
  </script>

  <template>
    <VPdfViewer v-bind="vpvProps" :worker-url="pdfWorker" />
  </template>
