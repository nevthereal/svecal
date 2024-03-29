<script lang="ts">
	import type { Dayjs } from 'dayjs';

	export let weekDay: string;
	export let date: Dayjs;
	export let index: number;
	export let offset: number;

	const todayNum = date.get('day');
	$: newDate = date.add(index - todayNum + 1 + offset * 7, 'day').date();
</script>

<div
	class={`p-4 flex gap-4 items-center justify-between select-none ${index != 0 && 'border-l-2'}`}
>
	<span class="font-bold text-xl">{weekDay}</span>
	<span
		class={`font-medium size-8  flex justify-center items-center rounded-full ${newDate === date.get('date') && 'bg-red-500 text-white'}`}
		>{newDate}</span
	>
</div>
