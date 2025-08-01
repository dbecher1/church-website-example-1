<script lang="ts">
	import '../app.css';
	import favicon from '$lib/assets/favicon.svg';
	import Logo from '$lib/assets/logo.svelte';
	import { Icon, Bars3, XMark } from 'svelte-hero-icons';
	import { fade, slide } from 'svelte/transition';

	let { children } = $props();

	let show = $state(false);
	const toggleShow = () => show = !show;

	const links = [
		{text: 'About', href: '/'},
		{text: 'Sermons', href: '/'},
		{text: 'Visit', href: '/'},
		{text: 'Events', href: '/'},
		{text: 'Give', href: '/'},
	]

	const footer_links = [
		{title: 'About Us', links: [
			{text: 'Our Story', href: ''},
			{text: 'Staff', href: ''},
			{text: 'Beliefs', href: ''},
			{text: 'Ministries', href: ''},
			{text: 'Legal Items', href: ''},
		]},
		{title: 'Learn More', links: [
			{text: 'Giving', href: ''},
			{text: 'Service', href: ''},
			{text: 'Community Outreach', href: ''},
			{text: 'Missions', href: ''},
			{text: 'Sponsor a Child', href: ''},
		]},
		{title: 'Contact Us', links: [
			{text: '1990 Hill Ave, Columbus, OH, 12345', href: ''},
			{text: 'church@the.hill', href: 'mailto:church@the.hill'},
			{text: '555-123-4567'}
		]}
	]
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<svelte:window on:wheel|nonpassive={e => {
	if (show) e.preventDefault();
}}/>

{#snippet sidebar()}
{#if show}
	<div role={'figure'} class='absolute top-0 left-0 bg-black/60 w-dvw h-dvh z-50' transition:fade onclick={toggleShow}></div>
	<div class='absolute top-0 right-0 h-dvh w-[45dvw] min-w-64 z-51 bg-base-100 flex p-6' transition:slide={{axis: 'x'}}>
		<div class='flex flex-col w-full mx-auto p1-'>
			<div class='flex flex-row justify-between'>
				<div class='flex flex-row gap-2 p-1'>
					<Logo class='size-8 fill-primary inline'/>
					<div class='text-lg mt-1'>The Hill</div>
				</div>
				<button onclick={toggleShow}>
					<Icon src={XMark} class='btn btn-ghost btn-sm px-1 fill-base-content'/>
				</button>
			</div>
			<nav class='flex flex-col p-2'>
			{#each [{text: 'Home', href: '/'}, ...links] as {text, href}}
				<a {href} class='link link-hover py-1 text-lg' onclick={toggleShow}>{text}</a>
			{/each}
		</nav>
		</div>
		
	</div>
{/if}
{/snippet}

{#snippet header()}
<nav class='grid grid-cols-3 w-full py-6 mx-auto'>
	
	<div class='mx-auto'>
		<a href='/'>
			<Logo class='fill-primary h-10 lg:h-12'/>
		</a>
	</div>
	
	<div class='flex justify-center'>
		<!-- <nav class='hidden flex gap-4'>
			{#each links as {text, href}}
				<a {href} class='btn btn-ghost btn-lg px-4 py-1 hover:text-primary whitespace-nowrap'>{text}</a>
			{/each}
		</nav> -->
	</div>

	<div class='mx-auto'>
		<a href='/' class='btn btn-ghost btn-lg px-4 py-1 hover:text-primary whitespace-nowrap'>Give</a>
		<button class='hidden btn btn-ghost btn-lg hover:text-primary' onclick={toggleShow}>
			Menu <Icon src={Bars3} class='size-6 lg:size-8 ml-1'/>
		</button>
	</div>
	
</nav>

{/snippet}

{#snippet footer()}
	<div class='footer sm:footer-horizontal py-10 px-14'>
		{#each footer_links as {title, links}}
			<nav>
				<h4 class='footer-title'>{title}</h4>
				{#each links as {text, href}}
					{#if href}
						<a {href} class='link link-hover'>{text}</a>
					{:else}
						<div class='link link-hover'>{text}</div>
					{/if}
				{/each}
			</nav>
		{/each}
	</div>
	<aside class='text-[9pt] flex flex-col px-14 py-8'>
		<div>&copy; 2025, The Hill, All Rights Reserved.</div>
		<div>Website by Daniel Becher.</div>
	</aside>
{/snippet}

<!-- CONTENT -->

{@render sidebar()}
<header class='max-w-[120rem] w-full mx-auto'>
	{@render header()}
</header>
<main class='flex-1 max-w-[120rem] w-full mx-auto relative flex flex-col overflow-x-hidden'>
	{@render children?.()}
</main>
<footer class='flex flex-col bg-neutral text-neutral-content'>
	{@render footer()}
</footer>
