<script lang="ts">
	import type { Dayjs } from 'dayjs';

	export let weekDay: string;
	export let today: Dayjs;
	export let index: number;

	const todayNum = today.get('day');
	const date = today.add(index - todayNum + 1, 'day').date();
</script>

<div class={`p-4 flex gap-4 items-center justify-between ${index != 0 && 'border-l-2'}`}>
	<span class={`font-bold text-xl ${index === todayNum - 1 && 'text-red-500'}`}>{weekDay}</span>
	<span class="">{date}</span>
</div>
