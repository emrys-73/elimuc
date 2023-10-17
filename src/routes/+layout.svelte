<script lang="ts">
	import '../app.postcss';
	import { AppShell } from '@skeletonlabs/skeleton';

	// Floating UI for Popups
	import { computePosition, autoUpdate, flip, shift, offset, arrow } from '@floating-ui/dom';
	import { storePopup } from '@skeletonlabs/skeleton';
	storePopup.set({ computePosition, autoUpdate, flip, shift, offset, arrow });
</script>


<AppShell class="bg-[#f3f3f3] relative w-full h-full">
	<!-- (header) -->
	<!-- <svelte:fragment slot="sidebarLeft">Sidebar Left</svelte:fragment> -->
	<!-- (sidebarRight) -->
	<!-- (pageHeader) -->
	<!-- Router Slot -->
	<slot />
	<!-- ---- / ---- -->
	<svelte:fragment slot="pageFooter">
		
		<!-- <div class="w-full h-36 absolute bottom-0 bg-green-500">
			Footer
		</div> -->
		<div class="w-full h-32 bg-[#f3f3f3] flex flex-col items-center justify-center p-6">
			Some footer text here as well aba hab kein Akku mehr
		</div>
	</svelte:fragment>
	<!-- (footer) -->
</AppShell>