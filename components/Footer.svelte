<script lang="ts">
	import { Separator } from '$shared/components/ui/separator/index.js';
	import { language } from '$shared/stores/language';

	let clazz = '';
	export { clazz as class };
	export let links: { [link: string]: { name: string; nameRu: string } } = {
		'https://ma.cyou/': { name: "Author's site", nameRu: 'Сайт Автора' }
	};
</script>

<footer
	class="{clazz !== ''
		? clazz + ' '
		: ''}flex flex-wrap justify-center gap-2 px-2 py-4 text-xs text-muted-foreground"
>
	{#each Object.entries(links) as [link, { name, nameRu }], i}
		<a href={link} class="hover:text-foreground">
			{$language === 'ru' ? nameRu : name}
		</a>
		{#if i < Object.entries(links).length - 1}
			<Separator orientation="vertical" class="bg-muted-foreground bg-opacity-50" />
		{/if}
	{/each}
</footer>
