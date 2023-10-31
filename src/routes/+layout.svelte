<script>
	import Analytics from '$lib/analytics.svelte';
</script>

<Analytics />
<header>
	<span>木野祭サーチ</span>
</header>
<main>
	<slot />
</main>

<footer>
	<a href="/">
		<img src="/icon/home.svg" alt="" />
		<span>Home</span>
	</a>
	<a href="/search">
		<img src="/icon/search.svg" alt="" />
		<span>ワード検索</span>
	</a>
</footer>

<style>
	header {
		position: sticky;
		background-color: #f3f3f3;
		top: 0;
		left: 0;
		width: calc(100lvw - 20px);
		padding: 0 10px;
		height: 50px;
		box-shadow: 0px 3px 2px -2px rgba(0, 0, 0, 0.2);
	}
	header span {
		font-weight: 700;
		line-height: 50px;
	}

	main {
		width: calc(100% - 50px);
		max-width: 800px;
		margin: 20px auto 70px auto;
	}

	footer {
		/* display: none; */
		width: 100lvw;
		height: 50px;
		display: flex;
		position: fixed;
		left: 0;
		bottom: 0;
		background-color: #f3f3f3;
	}
	footer a {
		display: flex;

		justify-content: center;
		align-items: center;
		width: 50%;
		height: 100%;
		text-decoration: none;
	}
	footer a img {
		width: 24px;
		height: 24px;
		margin: 0 10px 0 0;
	}
	footer a span {
		font-size: 18px;
		line-height: 18px;
	}
</style>
