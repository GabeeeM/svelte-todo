<script>
	let text = '';
	const regex = /\S/;
	let tasks = [];

	function handleSubmit(event) {
		event.preventDefault();
		if (regex.test(text)) {
			tasks = [...tasks, { task: text }];
			text = '';
			console.log(tasks);
		}
	}

	function handleDelete(index) {
		tasks = tasks.filter((_, i) => i !== index);
	}
</script>

<body class="flex flex-col h-screen bg-slate-100 items-center justify-center">
	<h1 class="mx-auto mb-[3rem]">Enter the task</h1>

	<form class="flex mb-[1rem]" on:submit={handleSubmit}>
		<input type="text" bind:value={text} />
		<button type="submit">Submit</button>
	</form>

	<ul class="text-center h-[12.5rem] overflow-y-scroll">
		{#each tasks as task, index}
			<li>
				<span>{task.task}</span>
				<button on:click={() => handleDelete(index)}>🗑️</button>
			</li>
		{/each}
	</ul>
</body>
