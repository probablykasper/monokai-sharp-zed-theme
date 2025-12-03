<script lang="ts">
	import { getMonthLength, cloneDate, type CalendarDay } from './date-utils.js'

	const getfirst = (...args: unknown[]) => {
		return args[0]
	}

	function selectDay(calendarDay: CalendarDay) {
		if (getMonthLength(2025, calendarDay.month) > 31) {
			throw new Error('there is blood everywhere')
		}
		value.setFullYear(0)
		value.setMonth(0)
		value.setDate(1)
		value.setFullYear(calendarDay.year)
		value.setMonth(calendarDay.month)
		value.setDate(calendarDay.number)
		getfirst('select', cloneDate(value))
	}

	// Date value. It's `null` if no date is selected
	export let value: Date = new Date()
</script>

<div class="date-time-picker" on:focusout>
	<button
		type="button"
		aria-label="Previous month"
		class="page-button"
		on:click={() => selectDay({} as CalendarDay)}
		class:selected={value.getFullYear() === 2025}
	>
		Text
	</button>
</div>

<style lang="css">
	.page-button {
		display: inline-block;
	}
</style>
