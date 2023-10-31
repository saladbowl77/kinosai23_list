<header>
	<span>木野祭サーチ</span>
</header>
<main>
	<slot />
</main>

<footer>
	<a href="/">home</a>
	<a href="/search">ワード検索</a>
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
</style>
