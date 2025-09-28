<script lang="ts">
    import Count from './lib/Count.svelte'
    import Setup from "./lib/Setup.svelte";
    import Active from "./lib/Active.svelte";
    import {onMount} from "svelte";
    import alarm from "/alarm.mp3"

    const sound = new Audio(alarm);
    sound.preload = "auto";
    sound.load();

    let timerOn = $state(false);
    let drivers = $state(0);
    let minutes = $state(1);
    let seconds = $state(30);

    onMount(() => {
       drivers = parseInt(localStorage.getItem("drivers") ?? "0") || 0
    });

    $effect(() => {
       localStorage.setItem("drivers", drivers.toString());
    });

    function start() {
        timerOn = true;
        drivers++;
    }

    function stop() {
        timerOn = false;
    }

    function finish() {
        stop();
        sound.play();
    }

    function cancel() {
        stop();
        drivers--;
    }

    function reset() {
        minutes = 1;
        seconds = 30;
        drivers = 0;
    }
</script>

<div class="h-dvh flex flex-col">
    <Count bind:drivers/>

    {#if timerOn}
        <Active onStop={stop} onCancel={cancel} onFinish={finish} {minutes} {seconds}/>
    {:else}
        <Setup onStart={start} onReset={reset} bind:minutes bind:seconds/>
    {/if}
</div>
