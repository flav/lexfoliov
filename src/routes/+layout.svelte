<script lang="ts">
	import '../app.css';
	import Gallery from '$lib/Gallery.svelte';
    import { slide } from 'svelte/transition';
    import { bounceInOut, bounceIn, bounceOut, cubicInOut, backInOut, sineInOut } from 'svelte/easing';
    import { afterNavigate } from '$app/navigation';
    import { base } from '$app/paths';
    import Logo from '$lib/assets/LEXLOGO-01.svg'
    import { layoutState } from '$lib/store.js';
    import Instagram from "$lib/assets/instagram.svg";
    import LinkedIn from "$lib/assets/linkedin.svg";

    let isDropdownHidden = $state(true);

    function toggleDropdown() {
        isDropdownHidden = !isDropdownHidden;
        console.log('dropdown triggered')
    }

    // Resets mobile nav dropdown on navigation
    afterNavigate(() => {
        isDropdownHidden = true;
    })
    // const navText = "text-3xl text-blue-700 pb-4 border-b border-blue-700";

	let { children } = $props();
</script>

<div class="lg:p-5 p-3 bg-amber-50 min-h-screen">
    <div class="border-2 border-slate-800 lg:px-20 lg:py-12 px-5">
        <!-- desktop -->
        <div class="hidden lg:grid grid-cols-4 gap-y-12 w-full mb-20">
            <!-- <div class="col-span-2">
                <a href="" class="h-16 w-16 block" aria-label="logo/homepage link">
                    <img src={Logo} alt="logo"/>
                </a>
            </div> -->
            <a href="{`${base}/`}" class="flex gap-x-10 group">
                <img src={Logo} alt="logo" class="w-16 h-16"/>
                <div class="">
                    <span class="text-xl lg:text-2xl xl:text-3xl text-slate-800 group-hover:font-semibold transition-all font-righteous">Alexsey daCosta</span>
                    <div class="w-full mt-4 border-b-2 border-slate-800 group-hover:w-[150%] transition-all"></div>
                </div>
            </a>
            <div></div>
            <div class="col-span-2 grid grid-cols-5 gap-x-4">
                <a href="{`${base}/portfolio`}" class="group col-span-2">
                    <span class="text-xl lg:text-2xl xl:text-3xl text-slate-800 group-hover:font-semibold transition-all font-righteous">My work</span>
                    <div class="w-2/3 group-hover:w-full mt-4 border-b-2 border-slate-800 transition-all"></div>
                </a>
                <div class="grid grid-cols-2 gap-x-4 col-span-3">
                    <a href="{`${base}/contact`}" class="group">
                        <span class="text-xl lg:text-2xl xl:text-3xl text-slate-800 group-hover:font-semibold transition-all font-righteous">Contact</span>
                        <div class="w-2/3 group-hover:w-full mt-4 border-b-2 border-slate-800 transition-all"></div>
                    </a>
                    <a href="{`${base}/about-me`}" class="group">
                        <span class="text-xl lg:text-2xl xl:text-3xl text-slate-800 group-hover:font-semibold transition-all font-righteous whitespace-nowrap">About me</span>
                        <div class="w-2/3 group-hover:w-full mt-4 border-b-2 border-slate-800 transition-all"></div>
                    </a>
                </div>
            </div>
        </div>
        <!-- mobile -->
        <div class="lg:hidden flex justify-between mt-2 mb-8 pb-2 border-b border-slate-800">
            <div>
                <a href="{`${base}/`}" class="flex items-center gap-x-10 group">
                    <img src={Logo} alt="logo" class="w-10 h-10"/>
                    <span class="col-span-3 text-xl text-slate-800 font-bold">Alexsey<br />daCosta</span>
                </a>
            </div>
            <button onclick={toggleDropdown} class="pl-5 cursor-pointer text-xl text-slate-800">
                {#if isDropdownHidden}
                    <!-- <i class="text-slate-800 text-xl fa-solid fa-bars"></i> -->
                     <span class="text-slate-800 text-5xl">+</span>
                {:else}
                    <!-- <i class="text-slate-800 text-xl fa-solid fa-xmark"></i> -->
                    <span class="text-slate-800 text-5xl inline-block transform rotate-45">+</span>
                {/if}
            </button>
        </div>
        {#if !isDropdownHidden}
            <div transition:slide={{duration: 500, easing:cubicInOut}}
             class="grid grid-cols-1 border-b-2 border-slate-800 mb-5">
                <a href="{`${base}/portfolio`}" class="mx-2 mt-2 pb-2 border-b border-slate-800 text-xl">My work</a>
                <a href="{`${base}/contact`}" class="mx-2 mt-2 pb-2 border-b border-slate-800 text-xl">Contact</a>
                <a href="{`${base}/about-me`}" class="mx-2 mt-2 pb-10  text-xl">About me</a>
            </div>
        {/if}
        <!-- <div class="lg:h-52"></div> filler -->
        <!-- <div class="grid grid-cols-1 md:grid-cols-2 gap-8">

        </div> -->

        <div class="flex items-center mb-15">
        <div class="md:text-xl text-sm font-righteous text-nowrap">{$layoutState.message}</div> <div class="ml-10 w-full border-b-2 border-slate-800"></div>
        </div>
        {@render children()}

        <!-- footer -->
        <div class="w-full">
            <div class="w-full mt-4 border-b-2 border-slate-800 group-hover:w-[150%] transition-all"></div>
            <div class="flex justify-between items-center my-5">
                <div class="flex gap-2">
                    <a href="https://www.instagram.com/alexseydc/" target="_blank">
                        <img class="h-8" alt="Instagram" src={Instagram}/>
                    </a>
                    <a href="https://www.linkedin.com/in/alexsey-dacosta-8a18b12b1/" target="_blank">
                        <img class="h-8" alt="LinkedIn" src={LinkedIn}/>
                    </a>
                </div>
                <a href="{`${base}/`}" class="">
                    <img src={Logo} alt="logo" class="w-10 h-10"/>
                </a>
            </div>
        </div>

    </div>
</div>

