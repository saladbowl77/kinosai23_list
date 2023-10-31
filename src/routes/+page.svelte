<script>
	import { browser } from '$app/environment';
	import shopList from './shopList.json';
	import Card from '$lib/component/card.svelte';

	let isRandom = false;
	let shownShopType = ['food', 'goods', 'special', 'fair', 'official', 'stage'];
	let showShopList = [];

	const updateList = () => {
		showShopList = [];
		for (const shopData of shopList) {
			if (!(shopData.type, shownShopType.includes(shopData.type))) continue;
			if (isRandom) {
				showShopList.splice(Math.floor(Math.random() * showShopList.length), 0, shopData);
			} else showShopList.push(shopData);
		}
	};

	if (browser) updateList();
</script>

<div id="selectCategory">
	<input
		class="hiddenCheckbox"
		type="checkbox"
		id="bind_food"
		bind:group={shownShopType}
		value="food"
		on:change={updateList}
	/>
	<label class="typeButton" id="button_food" for="bind_food">
		<img src="/icon/food.svg" alt="飲み物食べ物の画像" />
		<span>食べ物</span>
	</label>
	<input
		class="hiddenCheckbox"
		type="checkbox"
		id="bind_goods"
		bind:group={shownShopType}
		value="goods"
		on:change={updateList}
	/>
	<label class="typeButton" id="button_goods" for="bind_goods">
		<img src="/icon/goods.svg" alt="パレットの画像" />
		<span>グッズ</span>
	</label>
	<input
		class="hiddenCheckbox"
		type="checkbox"
		id="bind_special"
		bind:group={shownShopType}
		value="special"
		on:change={updateList}
	/>
	<label class="typeButton" id="button_special" for="bind_special">
		<img src="/icon/special.svg" alt="双眼鏡の画像" />
		<span>特殊模擬</span>
	</label>
	<!-- <input
		class="hiddenCheckbox"
		type="checkbox"
		id="bind_fair"
		bind:group={shownShopType}
		value="fair"
		on:change={updateList}
	/>
	<label class="typeButton" id="button_fair" for="bind_fair">
		<img src="/icon/fair.svg" alt="本の画像" />
		<span>キノフェア</span>
	</label> -->
	<input
		class="hiddenCheckbox"
		type="checkbox"
		id="bind_official"
		bind:group={shownShopType}
		value="official"
		on:change={updateList}
	/>
	<label class="typeButton" id="button_official" for="bind_official">
		<img src="/icon/official.jpg" alt="きーぼうの画像" />
		<span>公式イベント!</span>
	</label>
	<!-- <input
		class="hiddenCheckbox"
		type="checkbox"
		id="bind_stage"
		bind:group={shownShopType}
		value="stage"
		on:change={updateList}
	/>
	<label class="typeButton" id="button_stage" for="bind_stage">
		<img src="/icon/stage.svg" alt="マイクの画像" />
		<span>ステージ</span>
	</label> -->
</div>

<div class="switch-checkbox">
	<input type="checkbox" id="switch-check-1" bind:checked={isRandom} on:change={updateList} />
	<label for="switch-check-1">ランダム表示ON</label>
</div>

{#if showShopList.length == 0}
	データがありません
{:else}
	{#each showShopList as shopData}
		<Card {shopData} />
	{/each}
{/if}

<style>
	#selectCategory {
		display: flex;
		flex-wrap: wrap;
	}
	.typeButton {
		display: flex;
		gap: 5px;

		justify-content: center;
		align-items: center;
		width: calc(50% - 24px);
		height: 40px;
		border-radius: 10px;
		margin: 5px 10px;
	}
	@media screen and (max-width: 300px) {
		.typeButton {
			width: calc(100% - 24px);
			padding: 0 10px;
			justify-content: flex-start;
		}
	}

	.typeButton#button_food {
		background-color: #d6ffb5;
		border: solid 2px #a7e873;
	}
	.typeButton#button_goods {
		background-color: #ffb5b5;
		border: solid 2px #e87373;
	}
	.typeButton#button_special {
		background-color: #b5e6ff;
		border: solid 2px #73d5e8;
	}
	.typeButton#button_fair {
		background-color: #e9b5ff;
		border: solid 2px #cb73e8;
	}
	.typeButton#button_official {
		background-color: #ffe0b5;
		border: solid 2px #e8c373;
	}
	.typeButton#button_stage {
		background-color: #ffb5f8;
		border: solid 2px #e873da;
	}
	.typeButton img {
		width: 32px;
		height: 32px;
	}

	.hiddenCheckbox {
		display: none;
	}
	.hiddenCheckbox + label {
		opacity: 0.4;
	}
	.hiddenCheckbox:checked + label {
		opacity: 1;
	}

	.switch-checkbox {
		/* display: none; */
		display: flex;
		justify-content: flex-end;
		align-items: center;
	}
	.switch-checkbox input[type='checkbox'] {
		position: relative;
		cursor: pointer;
		width: 40px;
		height: 20px;
		border-radius: 60px;
		background-color: #ddd;
		-webkit-appearance: none;
		-moz-appearance: none;
		appearance: none;
		vertical-align: middle;
		transition: 0.5s;
	}

	.switch-checkbox input[type='checkbox']::before {
		position: absolute;
		top: 1px;
		left: 2px;
		width: 18px;
		height: 18px;
		box-sizing: border-box;
		border-radius: 50%;
		background: white;
		color: black;
		content: '';
		transition: 0.3s ease;
	}

	.switch-checkbox input[type='checkbox']:checked {
		background: #1ff210;
	}

	.switch-checkbox input[type='checkbox']:checked::before {
		left: 20px;
	}

	.switch-checkbox label {
		line-height: 26px;
	}
</style>
