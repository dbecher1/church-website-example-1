<script lang="ts">
    import Logo from '$lib/assets/logo.svelte';

    const services_ministries = [
        ['Sunday Worship', ['9 AM, 11 AM Sunday Morning']],
        ['Young Adults Ministry', ['7 PM Sunday Evening']],
        ["Ladies' Breakfast Study", ['10 AM, Tuesday Morning']],
        ['Middle School Youth', ['6 PM Wednesday Evening']],
        ['High School Youth', ['7 PM, Friday Evening']]
    ]
</script>

<svelte:head>
    <title>The Hill | Welcome Home</title>
</svelte:head>

{#snippet homepage_hero()}
    <div class='mt-6 mb-12 lg:my-20 w-full max-w-sm sm:max-w-md md:max-w-2xl lg:max-w-4xl mx-auto uppercase text-center flex flex-col'>
        <div class='py-0 text-3xl md:text-5xl/20 lg:text-7xl/22 font-bold'>
            Jesus <span class='text-primary'>loved</span> his community. <br class='md:hidden'>We do <span class='text-primary'>too.</span>
        </div>
        <div class='text-xl md:text-2xl lg:text-4xl font-semibold py-8 tracking-tight'>
            We are <span class='text-primary'>The Hill.</span>
        </div>
        <div class=''>
            <a href='/' class='btn btn-primary btn-outline not-md:btn-sm lg:btn-lg rounded-box'>Welcome Home</a>
        </div>
    </div>
{/snippet}

{#snippet homepage_bg()}
    <Logo class='w-5/12 absolute -z-1 top-0 left-1/2 -translate-x-1/2 fill-neutral/5'/>
    <Logo class='not-md:hidden w-5/12 absolute -z-1 top-0 left-1/12 -translate-x-1/2 fill-neutral/5'/>
    <Logo class='not-md:hidden w-5/12 absolute -z-1 top-0 left-11/12 -translate-x-1/2 fill-neutral/5'/>
{/snippet}

{#snippet info()}
    <div class='w-full bg-primary relative text-primary-content px-4 py-12 lg:p-20 grid grid-cols-1 lg:grid-cols-2 gap-8'>
        <Logo class='w-5/12 absolute z-1 top-0 left-1/2 lg:left-1/4 -translate-x-1/2 fill-primary-content/5 rotate-180'/>
        <Logo class='not-lg:hidden w-5/12 absolute z-1 top-0 left-3/4 -translate-x-1/2 fill-primary-content/5 rotate-180'/>
        <div class='text-3xl md:text-5xl/20 lg:text-7xl/22 font-bold z-2 text-center lg:text-right px-12'>
            At The Hill, we strive to love like <span class='text-neutral/90 bg-primary-content px-3'>Jesus.</span>
        </div>
        <div class='not-lg:hidden z-2 row-span-3'>
            <img src='/northview1.webp' alt='A woman worshipping in a purple sanctuary.' class='opacity-90'/>
        </div>
        <div class='text-xl md:text-2xl lg:text-4xl font-semibold z-2 text-center lg:text-right px-12'>
            He said, <span class='uppercase'>"come as you are,"</span> so no matter your history or walk, we would love for you to encounter this love.
        </div>
        <div class='mx-auto px-12 flex justify-center gap-12'>
            <a href='/' class='col-start-3 btn btn-base-100 btn-outline lg:btn-lg rounded-sm font-bold text-xl'>Learn More</a>
            <a href='/' class='col-start-3 btn btn-base-100 btn-outline lg:btn-lg rounded-sm font-bold text-xl'>Give Today</a>
        </div>
    </div>
    <div class='w-full bg-base-200 text-base-content p-4 mx-auto grid grid-cols-1 lg:grid-cols-2 relative'>
        <div class='not-lg:hidden p-24'>
            <img src='/worship.jpg' alt='A Worship and praise service.' class='opacity-90'/>
        </div>
        <div class='grid grid-cols-3 pb-8 px-12 lg:px-16 lg:py-8 gap-4 lg:gap-0'>
            <div class='text-2xl lg:text-4xl col-span-3 text-center place-items-center p-4 lg:p-8'>
                Services and Ministries
            </div>
            <hr class='not-lg:hidden col-span-3 opacity-30 not-lg:-mt-4'>
            {#each services_ministries as [service, time]}
                <div class='col-span-3 lg:col-span-2 not-lg:text-center text-xl lg:p-2'>{service}</div>
                <div class='col-span-3 lg:col-span-1 not-lg:text-center lg:text-lg p-1 lg:p-2'>{time}</div>
                <hr class='lg:hidden col-span-3 opacity-30'>
            {/each}
        </div>
    </div>
{/snippet}

<!-- CONTENT -->
{@render homepage_bg()}
{@render homepage_hero()}
{@render info()}