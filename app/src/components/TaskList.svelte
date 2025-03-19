<script lang="ts">
	import { fly } from 'svelte/transition';
	import { onMount } from 'svelte';

	let visible = $state(false);
	onMount(() => (visible = true));

	let { priority, tasks } = $props();
</script>

<div class="btn">
	{#if priority === 'High'}
		<button class="show" style="background-color: lightsalmon">{priority}</button>
	{:else if priority === 'Medium'}
		<button class="show" style="background-color: burlywood;">{priority}</button>
	{:else}
		<button class="show" style="background-color: lightseagreen;">{priority}</button>
	{/if}
</div>

<br />

{#if priority === 'High'}
	<div class="tasks" style="background-color: lightsalmon;">
		{#each tasks as task, index (task.id)}
			{#if visible}
				<div class="item" in:fly={{ x: 300, duration: 500, delay: index * 100 }}>
					<div class="task">
						{task.title}
					</div>
					<div class="done">
						<button class="done-btn">Done</button>
					</div>
				</div>
			{/if}
		{/each}
	</div>
{:else if priority === 'Medium'}
	<div class="tasks" style="background-color: burlywood;">
		{#each tasks as task, index (task.id)}
			{#if visible}
				<div class="item" in:fly={{ x: 300, duration: 500, delay: index * 100 }}>
					<div class="task">
						{task.title}
					</div>
					<div class="done">
						<button class="done-btn">Done</button>
					</div>
				</div>
			{/if}
		{/each}
	</div>
{:else}
	<div class="tasks" style="background-color: lightseagreen;">
		{#each tasks as task, index (task.id)}
			{#if visible}
				<div class="item" in:fly={{ x: 300, duration: 500, delay: index * 100 }}>
					<div class="task">
						{task.title}
					</div>
					<div class="done">
						<button class="done-btn">Done</button>
					</div>
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
		border-radius: 10px;
		padding: 2%;
		margin-left: 1%;
		margin-right: 1%;
	}

	.task {
		flex: 0 0 82%;
		background-color: white;
		border-radius: 7px;
		padding: 2%;
		margin: 0.45%;
		overflow-wrap: anywhere;
	}

	.item {
		display: flex;
	}

	.done {
		display: flex;
		flex: 0 0 10%;
		justify-content: center;
		align-items: center;
		float: right;
		margin-left: 2%;
	}

	.done-btn {
		color: black;
		border: none;
		border-radius: 7px;
		padding: 7px;
	}
</style>
