<script lang="ts">
	type Operator = '+' | '-' | '*' | '/';
	let num1 = 0;
	let num2 = 0;
	let op: Operator = '+';
	let res = 0;
	$: {
		if (op === '+') {
			res = num1 + num2;
		} else if (op === '-') {
			res = num1 - num2;
		} else if (op === '*') {
			res = num1 * num2;
		} else if (op === '/') {
			res = num1 / num2;
		}
	}
	function randomNumber() {
		num1 = Math.floor(Math.random() * 100);
		num2 = Math.floor(Math.random() * 100);

		const symbols: Operator[] = ['+', '-', '*', '/'];
		const idx = Math.floor(Math.random() * 4);

		op = symbols[idx];
	}
</script>

<h1 class="text-4xl">KALKULATOR</h1>
<input bind:value={num1} type="number" placeholder="0" />
<select bind:value={op}>
	<option value="+">+, plus</option>
	<option value="-">-, minus</option>
	<option value="*">*, krat</option>
	<option value="/">/, deljeno</option>
</select>
<input bind:value={num2} type="number" placeholder="0" />
<button class="p-3 bg-slate-600 text-white rounded-2xl hover:bg-slate-700" on:click={randomNumber}
	>RANDOM</button
>
<p>{num1} {op} {num2} = {res}</p>
