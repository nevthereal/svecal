<script lang="ts">
	import type { Dayjs } from 'dayjs';

	export let weekDay: string;
	export let date: Dayjs;
	export let index: number;
	export let offset: number;
	export let currentMonth: number;

	const todayNum = date.get('day');
	$: newDate = date.add(index - todayNum + 1 + offset * 7, 'day');
</script>

<div>
	<div
		class={`p-4 flex gap-4 items-center justify-between select-none ${index != 0 && 'border-l border-gray-200 dark:border-gray-600'} ${newDate.month() != currentMonth && 'text-gray-500 dark:text-gray-400'}`}
	>
		<span class="font-bold text-xl">{weekDay}</span>
		<span
			class={`font-medium size-8  flex justify-center items-center rounded-full ${newDate.toDate().toString() === date.toDate().toString() && 'bg-red-500 text-white'}`}
			>{newDate.date()}</span
		>
	</div>
	<div></div>
</div>
