<script lang="ts">
    import {onMount} from "svelte";

    interface Props {
        minutes: number;
        seconds: number;
        onEnd: () => void;
    }

    let {minutes, seconds, onEnd}: Props = $props();

    onMount(() => {
        update();
        const interval = setInterval(update, 1000);
        return () => clearInterval(interval);
    })

    function update() {
        if (seconds > 0) seconds--;
        else {
            if (minutes > 0) {
                minutes--;
                seconds = 59;
            } else {
                onEnd();
            }
        }
    }
</script>

<div class="countdown font-mono text-8xl">
    <span style="--value:{minutes};" aria-live="polite" aria-label={minutes.toString()}>{minutes}</span>
    :
    <span style="--value:{seconds};" aria-live="polite" aria-label={seconds.toString()}>{seconds}</span>
</div>