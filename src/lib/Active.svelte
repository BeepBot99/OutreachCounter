<script lang="ts">
    import Timer from "./Timer.svelte";

    interface Props {
        onStop: () => void;
        onCancel: () => void;
        onFinish: () => void;
        minutes: number;
        seconds: number;
    }

    let {onStop, onCancel, onFinish, minutes, seconds}: Props = $props();
</script>

<div class="flex-1 flex items-center justify-center">
    <Timer {minutes} {seconds} onEnd={onFinish}/>
</div>

<div class="dock bg-info text-info-content">
    <button type="button" onclick={onCancel}>
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor"
             class="size-[1.2em]">
            <path stroke-linecap="round" stroke-linejoin="round" d="M6 18 18 6M6 6l12 12"/>
        </svg>
        <span class="dock-label">Cancel</span>
    </button>

    <button type="button" onclick={onStop}>
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
             stroke="currentColor" class="size-[1.2em]">
            <path stroke-linecap="round" stroke-linejoin="round"
                  d="M5.25 7.5A2.25 2.25 0 0 1 7.5 5.25h9a2.25 2.25 0 0 1 2.25 2.25v9a2.25 2.25 0 0 1-2.25 2.25h-9a2.25 2.25 0 0 1-2.25-2.25v-9Z"/>
        </svg>
        <span class="dock-label">Stop</span>
    </button>
</div>