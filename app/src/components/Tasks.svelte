<script lang="ts">
	import TaskList from './TaskList.svelte';
	import data from './data.json';

	let tasks = data.tasks;

	let highTasks = [];
	let midTasks = [];
	let lowTasks = [];

	for (let i = 0; i < tasks.length; i++) {
		if (tasks[i].priority == 1) {
			highTasks.push(tasks[i]);
		} else if (tasks[i].priority == 2) {
			midTasks.push(tasks[i]);
		} else {
			lowTasks.push(tasks[i]);
		}
	}
</script>

<div class="container">
	<div class="item"><TaskList priority="High" tasks={highTasks} /></div>
	<div class="item"><TaskList priority="Medium" tasks={midTasks} /></div>
	<div class="item"><TaskList priority="Low" tasks={lowTasks} /></div>
</div>

<style>
	.container {
		background-color: beige;
		display: flex;
		border-radius: 7px;
		padding: 2%;
	}

	.item {
		flex: 1;
		align-items: center;
	}
</style>
