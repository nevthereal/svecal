<script lang="ts">
	import DayCell from '../cells/week/DayCell.svelte';
	import dayjs from 'dayjs';

	const weekDays = ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'];
	const today = dayjs();
</script>

<section class="w-full grid grid-cols-7 grid-rows-2">
	{#each weekDays as weekDay, idx}
		<DayCell {weekDay} index={idx} {today} />
	{/each}
</section>
