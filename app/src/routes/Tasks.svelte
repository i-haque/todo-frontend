<script>
	import TaskList from './TaskList.svelte';
</script>

<div class="container">
	<div class="item"><TaskList priority="High" /></div>
	<div class="item"><TaskList priority="Medium" /></div>
	<div class="item"><TaskList priority="Low" /></div>
</div>

<style>
	.container {
		background-color: beige;
		display: flex;
		align-items: flex-start;
		border-radius: 10px;
		padding: 2%;
	}

	.item {
		flex: 1;
		align-items: center;
	}
</style>
