<script>
	import shopList from '../shopList.json';
    import Card from '$lib/component/card.svelte';

	let isSearch = false;
	let searchText = '';
	let showShopList = [];

	const searchShop = () => {
		isSearch = true;
		showShopList = [];
		for (const shopData of shopList) {
			console.log(
				shopData.id.includes(searchText),
				shopData.text.includes(searchText),
				shopData.name.includes(searchText)
			);
			if (
				shopData.id.includes(searchText) ||
				shopData.text.includes(searchText) ||
				shopData.name.includes(searchText)
			)
				showShopList.push(shopData);
		}
	};
</script>

<div id="inputText">
	<input type="text" bind:value={searchText} placeholder="検索したいワードを入力してください" />
	<button on:click={searchShop}>検索</button>
</div>

{#if showShopList.length == 0 && isSearch}
	結果が見当たりません! 他のワードに変えて試してみてね!
{:else}
	{#each showShopList as shopData}
        <Card shopData={shopData}/>
	{/each}
{/if}

<style>
	input {
		margin: 0;
		padding: 0;
		background: none;
		border: none;
		border-radius: 0;
		outline: none;
		-webkit-appearance: none;
		-moz-appearance: none;
		appearance: none;
	}

	div#inputText {
		display: flex;
		flex-wrap: wrap;
		gap: 5px;
	}

	input[type='text'] {
		display: block;
		width: calc(100% - 40px - 70px);
		height: 30px;
		line-height: 30px;
		font-size: 18px;
		border-radius: 30px;
		padding: 0 10px;
		border: 2px solid #aeaeae;
	}

	button {
		border: none;
		width: 80px;
		min-width: 0;
		background-color: #9361d6;
		color: #fafafa;
		line-height: 20px;
		border-radius: 20px;
		font-size: 1.2rem;
		font-weight: bold;
		padding: 5px 0;
	}
</style>
