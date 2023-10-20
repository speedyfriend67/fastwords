<script lang="ts">
    import {words} from "./words";
    import {onMount} from "svelte";

    let word = ""
    let translated = ""
    let isTranslatedWordVisible = false

    const gen = () => {
        const entries = Object.entries(words)
        const randomIndex = Math.floor(Math.random() * entries.length)
        const [randomKey, randomValue] = entries[randomIndex]
        word = randomKey
        translated = randomValue
        isTranslatedWordVisible = false
    }

    onMount(gen)
</script>

<div class="h-screen flex items-center justify-center gap-x-16">
    <p class="font-bold text-5xl">{word.replace("_", " ")}</p>
    <button on:click={() => {isTranslatedWordVisible = true}} class="relative group">
        {#if !isTranslatedWordVisible}
            <div class="absolute top-0 left-0 w-full h-full bg-neutral-800 scale-125 rounded-xl z-20 hover:scale-125 transition">
            </div>
        {/if}
        <p class="font-bold text-5xl">{translated}</p>
    </button>
    <button on:click={() => gen()} class="fa-solid fa-rotate-right text-5xl hover:scale-125 active:scale-75 transition"></button>

</div>
<div class="fixed top-4 left-4">20분만에 만듦</div>

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.2/css/all.min.css" integrity="sha512-z3gLpd7yknf1YoNbCzqRKc4qyor8gaKU1qmn+CShxbuBusANI9QpRohGBreCFkKxLhei6S9CQXFEbbKuqLg0DA==" crossorigin="anonymous" referrerpolicy="no-referrer" />