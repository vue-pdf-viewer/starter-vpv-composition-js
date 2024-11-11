<script setup>
	import { ref, watch, onBeforeMount } from "vue";
	import { VPdfViewer, VPVBaseProps, useLicense } from "@vue-pdf-viewer/viewer";

	const props = defineProps({
		...VPVBaseProps,
		title: {
			type: String,
			required: true,
		},
	});

	onBeforeMount(() => {
		useLicense({ licenseKey: "your-license-key" });
	});

	const viewerRef = ref(null);

	watch(viewerRef, (newVal) => {
		console.log("These are VPV instance properties", Object.keys(newVal));
	});
</script>
<template>
	<div>
		<h2>
			{{ props.title }}
		</h2>
		<div :style="{ width: '1028px', height: '700px', margin: '0 auto' }">
			<VPdfViewer
				v-bind="props"
				ref="viewerRef" />
		</div>
	</div>
</template>
