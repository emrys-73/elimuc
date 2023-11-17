<script lang="ts">
	import '../app.postcss';
	import { AppShell } from '@skeletonlabs/skeleton';

	// Floating UI for Popups
	import { computePosition, autoUpdate, flip, shift, offset, arrow } from '@floating-ui/dom';
	import { storePopup } from '@skeletonlabs/skeleton';
	storePopup.set({ computePosition, autoUpdate, flip, shift, offset, arrow });
</script>


<AppShell class="">
	<!-- (header) -->
	<!-- <svelte:fragment slot="sidebarLeft">Sidebar Left</svelte:fragment> -->
	<!-- (sidebarRight) -->
	<!-- (pageHeader) -->
	<!-- Router Slot -->
	<slot />
	<!-- ---- / ---- -->
	<svelte:fragment slot="pageFooter">

		<div class="w-full h-32 bg-[#ffffff] text-black flex flex-col items-center justify-center p-6">
			<span class="opacity-60 font-serif">
				© Elim. All rights reserved
			</span>
		</div>
	</svelte:fragment>
	<!-- (footer) -->
</AppShell>