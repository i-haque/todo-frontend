<script>
	import { fly } from 'svelte/transition';

	let visible = $state(false);
	function onClick() {
		visible = true;
	}

	let { priority } = $props();

	let tasks = [
		{ id: 1, title: 'Buy Milk' },
		{ id: 2, title: 'Change drawing room settings' },
		{ id: 3, title: 'Take the trash can out' },
		{ id: 4, title: 'Finish the task' },
		{ id: 5, title: 'Take the dog out' },
		{ id: 6, title: 'Configure dev env' },
		{ id: 7, title: 'Configure packages and dependencies' },
		{ id: 8, title: 'Code' }
	];
</script>

<div class="btn">
	{#if priority === 'High'}
		<button class="show" style="background-color: lightsalmon;" onclick={onClick}>{priority}</button
		>
	{:else if priority === 'Medium'}
		<button class="show" style="background-color: burlywood;" onclick={onClick}>{priority}</button>
	{:else}
		<button class="show" style="background-color: lightseagreen;" onclick={onClick}
			>{priority}</button
		>
	{/if}
</div>

<br />

{#if priority === 'High'}
	<div class="tasks" style="background-color: lightsalmon;">
		{#each tasks as task, index (task.id)}
			{#if visible}
				<div class="task" in:fly={{ x: 300, duration: 500, delay: index * 100 }}>
					{task.title}
				</div>
			{/if}
		{/each}
	</div>
{:else if priority === 'Medium'}
	<div class="tasks" style="background-color: burlywood;">
		{#each tasks as task, index (task.id)}
			{#if visible}
				<div class="task" in:fly={{ x: 300, duration: 500, delay: index * 100 }}>
					{task.title}
				</div>
			{/if}
		{/each}
	</div>
{:else}
	<div class="tasks" style="background-color: lightseagreen;">
		{#each tasks as task, index (task.id)}
			{#if visible}
				<div class="task" in:fly={{ x: 300, duration: 500, delay: index * 100 }}>
					{task.title}
				</div>
			{/if}
		{/each}
	</div>
{/if}

<style>
	.btn {
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.show {
		/* background-color: ; */
		padding: 12px;
		color: white;
		border: none;
		border-radius: 5px;
	}

	.tasks {
		background-color: antiquewhite;
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		border-radius: 10px;
		padding: 2%;
		margin-left: 1%;
		margin-right: 1%;
	}

	.task {
		background-color: white;
		border-radius: 10px;
		padding: 2%;
		margin: 0.25%;
	}
</style>
