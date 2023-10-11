

下面这个例子是 Modal 嵌套 Form，并从两者调用处理函数的示例。

App.svelte

```
<script>
	import Form from "./Form.svelte"
	import Modal from "./Modal.svelte"
	
	let showModal = false;
	let saveForm
</script>

<button on:click="{() => showModal = !showModal}">
	toggle modal
</button>

{#if showModal}
	<br/><br/><br/>(don't mind Modal style, it's an example)<br/><br/><br/>
	<Modal on:click={saveForm}>
		<Form bind:saveForm/>
	</Modal>
{/if}
```

Modal.svelte

```
<div>
	<slot/>
	<br/><br/>(I wanna use this button in Modal instead to save the form)<br/><br/>
	<button on:click>
		Save Form from Outside
	</button>
	<br/><br/>How to?
</div>
```

Form.svelte

```
<script>
	export function saveForm() {
		alert("Form saved! Name: " + value)
	}
	
	let value = '';
</script>

<form on:submit|preventDefault={saveForm}>
	Name: <input id="name" bind:value>
	<button type="submit">
		Save Form from Inside
	</button>
</form>
```

来源：[Save form from Modal (parent to child dispatch)](https://svelte.dev/repl/8b31ce8832b44599980096eab56e7264?version=4.2.1)


