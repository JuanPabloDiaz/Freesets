<script>
	import Assets from '@/components/Assets.svelte';
	import assets from '@/store.js';
	import { page } from '$app/stores';
	import { queryParameters } from 'sveltekit-search-params';
	const params = queryParameters();
	const { category } = $derived($page.params);

	assets.changeCategory(category);
	if ($params.q) assets.search($params.q);
	if ($params.page) assets.changePage($params.page);

	$effect(() => {
		assets.changeCategory(category);
		if ($params.q) assets.search($params.q);
		if ($params.page) assets.changePage($params.page);
	});

	const og = {
		image: `https://res.cloudinary.com/cosmocloudinary/image/upload/f_auto,q_auto/v1/freesets/og/${$assets.nameID}`,
		description: `Explore a collection of the best free ${$assets.name} resources/assets for your next project.`,
		title: $assets.name + ' - Freesets',
		icon: `data:image/svg+xml,%3Csvg width='205' height='205' fill='%23${$assets.color?.slice(1)}xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='m102.5 126.661 18.792 11.226c1.789 1.139 3.537 1.1 5.242-.117s2.317-2.887 1.835-5.008l-4.881-21.232 16.595-14.399c1.627-1.464 2.115-3.212 1.465-5.242-.651-2.03-2.115-3.13-4.393-3.3l-21.72-1.708-8.542-20.256c-.814-1.952-2.278-2.929-4.393-2.929-2.115 0-3.58.977-4.393 2.929l-8.541 20.256-21.72 1.708c-2.279.163-3.743 1.263-4.394 3.3-.65 2.037-.162 3.784 1.465 5.242l16.595 14.399-4.881 21.232c-.488 2.115.124 3.784 1.835 5.008 1.712 1.223 3.46 1.262 5.242.117l18.792-11.226Zm-32.702 53.934h-25.87c-5.368 0-9.966-1.913-13.793-5.74-3.827-3.826-5.737-8.421-5.73-13.784v-25.869L5.613 116.167c-1.79-1.953-3.173-4.107-4.149-6.463S0 104.947 0 102.5c0-2.44.488-4.842 1.464-7.204.976-2.363 2.36-4.517 4.15-6.463l18.79-19.035v-25.87c0-5.368 1.914-9.966 5.74-13.793 3.827-3.827 8.422-5.737 13.785-5.73h25.869L88.833 5.613c1.953-1.79 4.11-3.173 6.472-4.149C97.668.488 100.066 0 102.5 0c2.44 0 4.842.488 7.204 1.464 2.363.976 4.517 2.36 6.463 4.15l19.035 18.79h25.869c5.369 0 9.967 1.914 13.794 5.74 3.827 3.827 5.737 8.422 5.73 13.785v25.869l18.792 19.035c1.79 1.953 3.173 4.11 4.149 6.472.976 2.363 1.464 4.761 1.464 7.195 0 2.44-.488 4.842-1.464 7.204-.976 2.363-2.359 4.517-4.149 6.463l-18.792 19.035v25.869c0 5.369-1.913 9.967-5.74 13.794-3.826 3.827-8.421 5.737-13.784 5.73h-25.869l-19.035 18.792c-1.953 1.79-4.107 3.173-6.463 4.149S104.947 205 102.5 205c-2.44 0-4.839-.488-7.195-1.464-2.355-.976-4.513-2.359-6.472-4.149l-19.035-18.792Z' /%3E%3C/svg%3E`
	};
</script>

<svelte:head>
	<title>{$assets.name} - Freesets</title>
	<meta name="theme-color" content={$assets.color} />
	<meta name="view-transition" content="same-origin" />
	<meta name="robots" content="index, follow" />
	<meta name="author" content="Cosmo" />
	<link rel="icon" href={og.icon} />
	<meta name="description" content={og.description} />
	<link rel="canonical" href="https://freesets.dev/{$assets.nameID}" />

	<!-- Open Graph -->
	<meta property="og:title" content={og.title} />
	<meta property="og:site_name" content={og.title} />
	<meta property="og:type" content="website" />
	<meta property="og:image" content={og.image} />
	<meta property="og:url" content="https://freesets.dev/{$assets.nameID}" />
	<meta property="og:description" content={og.description} />

	<!-- Twitter -->
	<meta name="twitter:card" content="summary_large_image" />
	<meta name="twitter:creator" content="@CosmoArt0" />
	<meta name="twitter:title" content={og.title} />
	<meta name="twitter:description" content={og.description} />
	<meta name="twitter:image" content={og.image} />
</svelte:head>

<Assets />
