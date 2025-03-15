<script lang="ts">
	let hour = new Date().getHours();
</script>

{#if hour < 12}
	<div class="greet">
		<h1 class="message">Good Morning!</h1>
	</div>
{:else if hour < 18}
	<div class="greet">
		<h1 class="message">Good Afternoon!</h1>
	</div>
{:else}
	<div class="greet">
		<h1 class="message">Good Evening!</h1>
	</div>
{/if}

<style>
	.greet {
		display: flex;
		justify-content: center;
		align-content: center;
		border-radius: 10px;
	}
</style>
