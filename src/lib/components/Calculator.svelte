<script>
	import Display from './Display.svelte';
	import KeyBoard from './keyboard.svelte';

	let displayValue = '';
	let previousValue = '';
	let currentValue = '';
	let operator = '';
	function updateDisplay(e) {
		const value = e.target.value;

		if (Number(value) >= 0 && Number(value) < 10) {
			currentValue += value;
			displayValue = currentValue;
		}

		switch (value) {
			case 'ac':
				displayValue = '';
				currentValue = '';
				previousValue = '';
				break;
			case 'plusminus':
				currentValue = currentValue * -1;
				displayValue = currentValue;
				break;
			case 'percent':
				currentValue = currentValue / 100;
				displayValue = currentValue;
				break;
			case 'dot':
				if (!currentValue.includes('.')) {
					currentValue += '.';
					displayValue = currentValue;
					break;
				}
			case '+':
			case '-':
			case '*':
			case '/':
				if (previousValue && currentValue) {
					calculate();
				}
				operator = value;
				previousValue = currentValue;
				currentValue = '';
				break;
			case '=':
				if (previousValue && currentValue) {
					calculate();
					operator = '';
					previousValue = '';
				}
		}
		function calculate() {
			let prev = parseFloat(previousValue);
			let current = parseFloat(currentValue);
			let result;
			switch (operator) {
				case '+':
					result = prev + current;
					console.log(result);
					break;
				case '-':
					result = prev - current;
					break;
				case '*':
					result = prev * current;
					break;
				case '/':
					result = prev / current;
					break;
			}
			displayValue = result.toString();
			currentValue = result.toString();
			previousValue = '';
		}
	}
</script>

<fieldset class="calculator">
	<legend>KeyBoard</legend>
	<input type="text" value={operator}{displayValue} disabled />
	<KeyBoard on:click={updateDisplay} />
</fieldset>

<style lang="scss">
	.calculator {
		margin: 0 auto;
		border: 2px solid #333;
		border-radius: 10px;
		padding: 20px;
		background-color: #f0f0f0;
		box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
		max-width: 300px;
		// Add this to ensure proper sizing
		box-sizing: border-box;

		input {
			margin-bottom: 2rem;
			width: 100%;
			// Adjust padding and add box-sizing
			padding: 10px;
			box-sizing: border-box;
			font-size: 1.5rem;
			text-align: right;
			border: 1px solid #ccc;
			border-radius: 5px;
			background-color: #fff;
			box-shadow: inset 0 1px 3px rgba(0, 0, 0, 0.1);
		}
	}
</style>
