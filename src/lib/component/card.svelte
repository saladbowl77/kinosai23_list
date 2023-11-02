<script>
	import Place from '$lib/component//place.svelte';
	export let shopData = {
		id: '',
		type: '',
		name: '',
		text: '',
		map: {
			src: '/map1.jpg',
			x: '',
			y: ''
		}
	};
</script>

<div>
	<input type="checkbox" id="contentBox_{shopData.id}" class="contentBoxCB" on:change={gtag('event',`click_shop_card${shopData.id}`)}/>
	<label class="contentBox type_{shopData.type}" for="contentBox_{shopData.id}">
		<p class="contentBox_title type_{shopData.type}">{shopData.name}</p>
		<p>{shopData.text}</p>
		<p>場所 : {shopData.id}</p>
		{#if shopData.map}
			<Place src={shopData.map.src} x={shopData.map.x} y={shopData.map.y} />
		{/if}
	</label>
</div>

<style>
	.contentBoxCB {
		display: none;
	}
	label.contentBox {
		display: block;
		color: #333333;
		background-color: #f7f7f7;
		width: calc(100% - 40px);
		max-width: 800px;
		margin: 20px auto;
		padding: 15px;
		height: 100px;
		border-radius: 3px;
		box-shadow: 2px 2px 10px -2px rgba(0, 0, 0, 0.45);
	}
	.contentBox_title {
		position: relative;
		font-weight: 600;
		font-size: 1.3rem;
		line-height: 1.5em;
		padding-left: 1.4rem;
	}
	.contentBox_title::before {
		position: absolute;
		top: 0.2rem;
		left: 0;
		content: '';
		display: inline-block;
		width: 1.1rem;
		height: 1.1rem;
		background-size: contain;
		vertical-align: middle;
	}
	.contentBox_title.type_food::before {
		background-image: url('/icon/food.svg');
	}
	.contentBox_title.type_goods::before {
		background-image: url('/icon/goods.svg');
	}
	.contentBox_title.type_special::before {
		background-image: url('/icon/special.svg');
	}
	.contentBox_title.type_official::before {
		background-image: url('/icon/official.jpg');
	}
	.contentBox_title.type_stage::before {
		background-image: url('/icon/stage.svg');
	}

	.contentBoxCB + label.contentBox {
		height: 60px;
		overflow: hidden;
		position: relative;
	}
	.contentBoxCB + label.contentBox::after {
		position: absolute;
		bottom: 0;
		left: 0;
		content: '';
		width: 100%;
		height: 40px;
		background: -moz-linear-gradient(180deg, rgba(247, 247, 247, 0) 0%, rgba(247, 247, 247, 1) 45%);
		background: -webkit-linear-gradient(
			180deg,
			rgba(247, 247, 247, 0) 0%,
			rgba(247, 247, 247, 1) 45%
		);
		background: linear-gradient(180deg, rgba(247, 247, 247, 0) 0%, rgba(247, 247, 247, 1) 45%);
	}
	.contentBoxCB:checked + label.contentBox {
		height: fit-content;
	}
	.contentBoxCB:checked + label.contentBox::after {
		display: none;
	}

	.contentBox.type_food {
		background-color: rgb(235, 255, 219);
	}
	.contentBoxCB + label.contentBox.type_food::after {
		background: -moz-linear-gradient(180deg, rgba(235, 255, 219, 0) 0%, rgba(235, 255, 219, 1) 45%);
		background: -webkit-linear-gradient(
			180deg,
			rgba(235, 255, 219, 0) 0%,
			rgba(235, 255, 219, 1) 45%
		);
		background: linear-gradient(180deg, rgba(235, 255, 219, 0) 0%, rgba(235, 255, 219, 1) 45%);
	}
	.contentBox.type_goods {
		background-color: rgb(255, 229, 229);
	}
	.contentBoxCB + label.contentBox.type_goods::after {
		background: -moz-linear-gradient(180deg, rgba(255, 229, 229, 0) 0%, rgba(255, 229, 229, 1) 45%);
		background: -webkit-linear-gradient(
			180deg,
			rgba(255, 229, 229, 0) 0%,
			rgba(255, 229, 229, 1) 45%
		);
		background: linear-gradient(180deg, rgba(255, 229, 229, 0) 0%, rgba(255, 229, 229, 1) 45%);
	}
	.contentBox.type_special {
		background-color: rgb(235, 248, 255);
	}
	.contentBoxCB + label.contentBox.type_special::after {
		background: -moz-linear-gradient(180deg, rgba(235, 248, 255, 0) 0%, rgba(235, 248, 255, 1) 45%);
		background: -webkit-linear-gradient(
			180deg,
			rgba(235, 248, 255, 0) 0%,
			rgba(235, 248, 255, 1) 45%
		);
		background: linear-gradient(180deg, rgba(235, 248, 255, 0) 0%, rgba(235, 248, 255, 1) 45%);
	}
	.contentBox.type_fair {
		background-color: rgb(246, 224, 255);
	}
	.contentBoxCB + label.contentBox.type_fair::after {
		background: -moz-linear-gradient(180deg, rgba(246, 224, 255, 0) 0%, rgba(246, 224, 255, 1) 45%);
		background: -webkit-linear-gradient(
			180deg,
			rgba(246, 224, 255, 0) 0%,
			rgba(246, 224, 255, 1) 45%
		);
		background: linear-gradient(180deg, rgba(246, 224, 255, 0) 0%, rgba(246, 224, 255, 1) 45%);
	}
	.contentBox.type_official {
		background-color: rgb(255, 244, 230);
	}
	.contentBoxCB + label.contentBox.type_official::after {
		background: -moz-linear-gradient(180deg, rgba(255, 244, 230, 0) 0%, rgba(255, 244, 230, 1) 45%);
		background: -webkit-linear-gradient(
			180deg,
			rgba(255, 244, 230, 0) 0%,
			rgba(255, 244, 230, 1) 45%
		);
		background: linear-gradient(180deg, rgba(255, 244, 230, 0) 0%, rgba(255, 244, 230, 1) 45%);
	}
	.contentBox.type_stage {
		background-color: rgb(255, 226, 252);
	}
	.contentBoxCB + label.contentBox.type_stage::after {
		background: -moz-linear-gradient(180deg, rgba(255, 226, 252 0) 0%, rgba(255, 226, 252 1) 45%);
		background: -webkit-linear-gradient(
			180deg,
			rgba(255, 226, 252 0) 0%,
			rgba(255, 226, 252 1) 45%
		);
		background: linear-gradient(180deg, rgba(255, 226, 252, 0) 0%, rgba(255, 226, 252, 1) 45%);
	}
</style>
