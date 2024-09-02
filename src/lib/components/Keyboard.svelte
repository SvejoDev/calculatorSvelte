<section>
	<button value="ac" on:click class="operator">clear</button>
	<button value="plusminus" on:click class="operator">±</button>
	<button value="percent" on:click class="operator">%</button>
	<button value="/" on:click class="operator">÷</button>

	<button value="7" on:click>7</button>
	<button value="8" on:click>8</button>
	<button value="9" on:click>9</button>
	<button value="*" on:click class="operator">×</button>

	<button value="4" on:click>4</button>
	<button value="5" on:click>5</button>
	<button value="6" on:click>6</button>
	<button value="-" on:click class="operator">−</button>

	<button value="1" on:click>1</button>
	<button value="2" on:click>2</button>
	<button value="3" on:click>3</button>
	<button value="+" on:click class="operator">+</button>

	<button value="0" on:click class="span-two">0</button>
	<button value="dot" on:click>.</button>
	<button value="=" on:click class="operator">=</button>
</section>

<style lang="scss">
	section {
		display: grid;
		grid-template-columns: repeat(4, 1fr);
		gap: 1px;

		button {
			font-size: 1rem;
			font-weight: bold;
			width: 100%;
			height: 60px;
			border: none;
			background-color: #e0e0e0;
			color: #333;
			cursor: pointer;
			transition: background-color 0.2s;

			&:hover {
				opacity: 0.8;
			}

			&.operator {
				background-color: #ff9f0a;
				color: #fff;
			}

			&.span-two {
				grid-column: span 2;
				border-radius: 0 0 0 10px;
			}

			&:last-child {
				border-radius: 0 0 10px 0;
			}

			&:nth-child(13),
			&:nth-child(14),
			&:nth-child(15) {
				border-radius: 0;
			}
		}
	}
</style>
