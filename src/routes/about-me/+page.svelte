<script>
    import Me from '$lib/assets/about-me/MEPICTURE.jpg'
    import { layoutState } from '$lib/store.js';

    layoutState.set({ message: 'About me' });

</script>

<div class="grid lg:grid-cols-2 grid-cols-1 justify-items-center gap-15 lg:gap-40">
    <div class="max-w-2xl mx-auto">
        <!-- <img src={Me} alt="me" class="border-2 border-slate-800 max-w-lg justify-self-end"/> -->
        <img src={Me} alt="me"
            class="border-2 border-slate-800 w-64 md:w-96 lg:w-full h-auto"
        />
    </div>
    <p class="text-lg lg:text-xl place-self-center justify-self-start max-w-xl font-lexend">
        Hi! My name is Alexsey daCosta and I am a Graphic Designer. I have a BA from the University of Michigan where I studied Art & Design.
        <br><br>
        I am passionate about the environment and all things creative. In my free time you can find me taking walks, birdwatching, or playing video games.
        <br><br>
        If you like what you see I would love to work with you!
    </p>
</div>