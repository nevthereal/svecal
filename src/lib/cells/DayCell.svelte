<script lang="ts">
	export let day: string;
	export let index: number;
	export let weekDay: number;
</script>

<div class={`p-4 ${index != 0 ? 'border-l-2' : ''}`}>
	<span class={`font-bold text-xl ${index === weekDay - 1 ? 'text-red-500' : ''}`}>{day}</span>
</div>
