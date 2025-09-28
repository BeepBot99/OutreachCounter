<script lang="ts">
    interface Props {
        drivers: number;
    }

    let {drivers = $bindable()}: Props = $props();
</script>

<div class="navbar bg-neutral text-neutral-content justify-between items-center p-0">
    <button class="btn btn-square aspect-square h-full w-auto bg-success text-success-content"
            aria-label="Increment Drivers"
            onclick={() => drivers++}>
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor"
             class="size-8">
            <path stroke-linecap="round" stroke-linejoin="round" d="M12 4.5v15m7.5-7.5h-15"/>
        </svg>
    </button>
    <div class="flex items-center gap-2">
        <strong class="text-4xl">{drivers}</strong>
        <span class="text-3xl">drivers</span>
    </div>
    <button class="btn btn-square aspect-square h-full w-auto bg-error text-error-content"
            aria-label="Decrement Drivers"
            onclick={() => drivers = Math.max(drivers - 1, 0)}
            disabled={drivers <= 0}>
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor"
             class="size-8">
            <path stroke-linecap="round" stroke-linejoin="round" d="M5 12h14"/>
        </svg>
    </button>
</div>

