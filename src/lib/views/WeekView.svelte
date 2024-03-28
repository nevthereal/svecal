<script lang="ts">
	import DayCell from '../cells/DayCell.svelte';

	const weekDays = ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'];
	const day = new Date();
	const weekDay = day.getDay();
</script>

<section class="w-full grid grid-cols-7 grid-rows-5">
	{#each weekDays as day, idx}
		<DayCell {day} index={idx} {weekDay} />
	{/each}
</section>
