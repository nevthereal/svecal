<script lang="ts">
	import { writable } from 'svelte/store';
	import DayCell from '../cells/week/DayCell.svelte';
	import dayjs from 'dayjs';

	const weekDays = ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'];
	const months = [
		'January',
		'February',
		'March',
		'April',
		'May',
		'June',
		'July',
		'August',
		'September',
		'October',
		'November',
		'December'
	];

	const today = dayjs();

	let offset = 0;

	const setOffset = (newOffset: number) => {
		if (newOffset === 0) {
			offset = 0;
		}
		offset += newOffset;
	};
</script>

<main class="p-6">
	<section class="w-full flex justify-between">
		<h1 class="text-3xl font-black">{months[today.add(offset * 7, 'day').month()]}</h1>
		<div class="flex gap-2">
			<button on:click={() => setOffset(-1)}>
				<svg
					xmlns="http://www.w3.org/2000/svg"
					viewBox="0 0 24 24"
					fill="currentColor"
					class="w-6 h-6"
				>
					<path
						fill-rule="evenodd"
						d="M7.72 12.53a.75.75 0 0 1 0-1.06l7.5-7.5a.75.75 0 1 1 1.06 1.06L9.31 12l6.97 6.97a.75.75 0 1 1-1.06 1.06l-7.5-7.5Z"
						clip-rule="evenodd"
					/>
				</svg>
			</button>
			<button on:click={() => setOffset(0)}>Today</button>
			<button on:click={() => setOffset(1)}>
				<svg
					xmlns="http://www.w3.org/2000/svg"
					viewBox="0 0 24 24"
					fill="currentColor"
					class="w-6 h-6"
				>
					<path
						fill-rule="evenodd"
						d="M16.28 11.47a.75.75 0 0 1 0 1.06l-7.5 7.5a.75.75 0 0 1-1.06-1.06L14.69 12 7.72 5.03a.75.75 0 0 1 1.06-1.06l7.5 7.5Z"
						clip-rule="evenodd"
					/>
				</svg>
			</button>
		</div>
	</section>
	<section class="w-full grid grid-cols-7 grid-rows-2">
		{#each weekDays as weekDay, idx}
			<DayCell {offset} {weekDay} index={idx} {today} />
		{/each}
	</section>
</main>

<style>
	button {
		@apply bg-gray-200 rounded-lg p-2 active:scale-95;
	}
</style>
