<script>
	import shopList from '../shopList.json';

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
    <input type="text" bind:value={searchText} placeholder="検索したいワードを入力してください"/>
<button on:click={searchShop}>検索</button>
</div>

{#if showShopList.length == 0 && isSearch}
	結果が見当たりません! 他のワードに変えて試してみてね!
{:else}
	{#each showShopList as shopData}
    <input type="checkbox" id="contentBox_{shopData.id}" class="contentBoxCB" />
    <label class="contentBox type_{shopData.id}" for="contentBox_{shopData.id}">
        <p class="contentBox_title">{shopData.name}</p>
        <p>{shopData.text}</p>
        <p>場所 : {shopData.id}</p>
    </label>
	{/each}
{/if}

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
		font-weight: 600;
		font-size: 1.3rem;
		line-height: 1.5em;
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
        background: -moz-linear-gradient(180deg, rgba(247,247,247,0) 0%, rgba(247,247,247,1) 45%);
        background: -webkit-linear-gradient(180deg, rgba(247,247,247,0) 0%, rgba(247,247,247,1) 45%);
        background: linear-gradient(180deg, rgba(247,247,247,0) 0%, rgba(247,247,247,1) 45%);
    }
	.contentBoxCB:checked + label.contentBox {
		height: fit-content;
	}
    .contentBoxCB:checked + label.contentBox::after {display: none;
    }
    
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

    input[type="text"] {
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
