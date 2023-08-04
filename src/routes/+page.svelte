<script lang="ts">
	import dayjs from 'dayjs';
    import Day from '../components/day.svelte';	
    import Modal from '../components/modal.svelte';	
	let currentMonth = dayjs();
    let showModal = false;
    let clickedDay = 0;
    function showDay(e: CustomEvent<any>){
        console.log(e);
        clickedDay = e.detail;
        showModal = true;
    }
</script>

{#if showModal}
<Modal on:close={() => showModal = false}>{clickedDay}</Modal>
{/if}

<h1>{currentMonth.format('YYYY')}</h1>
<div style="display: flex; align-items:center; gap:20px">
	<button on:click={() => (currentMonth = currentMonth.subtract(1, 'month'))}>Prev</button>
	<h2>{currentMonth.format('MMMM')}</h2>
	<button on:click={() => currentMonth = currentMonth.add(1, 'month')}>Next</button>
</div>

<div class="day-container">
{#each {length: currentMonth.daysInMonth()} as _, i}
    <Day dayNumber="{i+1}" on:show-day={e => showDay(e)}></Day>
{/each}
</div>

<style>
    .day-container{
        display: flex;
        flex-wrap: wrap;
        gap: 10px
    }
    button{
        height: auto;
    }
</style>
