<script>
	export let src, x, y;
</script>

<div class="mapWrap">
	<div class="mapImg" style="background-image: url({src});">
		<div class="mapPoint" style="top: {x};left: {y};" />
	</div>
</div>

<style>
	.mapImg {
		position: relative;
		width: 100%;
		max-width: 500px;
		aspect-ratio: 4/3;
		margin: 0 auto;
		background-size: contain;
	}
	.mapPoint {
		position: absolute;
		width: 6%;
		height: 4%;
		border-radius: 20px;
		border: 5px solid #1279ff;
	}
</style>
