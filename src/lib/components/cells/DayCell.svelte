<script lang="ts">
	export let weekDay: string;
	export let today: Date;
	export let index: number;

	const todayNum = today.getDay();
</script>

<div class={`p-4 ${index != 0 && 'border-l-2'}`}>
	<span class={`font-bold text-xl ${index === todayNum - 1 && 'text-red-500'}`}>{weekDay}</span>
</div>
