<script lang="ts">
    type ImageType = {
        title: string;
        src: string;
    }

    export let images: ImageType[];

</script>


<ul class="flex overflow-x-auto gap-6 snap-x snap-mandatory before:shrink-0 before:w-[30vw] after:shrink-0 after:w-[30vw]">

    {#each images as {title, src}}
        <li class="shrink-0 snap-center relative">

            
            <img {title} {src} alt={title} class="h-[70vh] rounded-2xl">
            
            
        </li>
    {/each}
</ul>
