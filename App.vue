<script>
export default {
	onLaunch: function () {
		console.log('App Launch')
	},
	onShow: function () {
		console.log('App Show')
	},
	onHide: function () {
		console.log('App Hide')
	}
}
</script>

<style>
:root {
	--black: #1E0D02;
	--yellow: #FFE471;
	--yellow-deep: #FFE471;
	--brown: #93774E;
}

body {
	min-height: 100%;
	/* background: linear-gradient(to bottom, #1C1A1A, #1C1A1A); */
	/* background: rgba(23, 23, 23, .7); */
	/* background: linear-gradient(100deg, #1C1A1A 0,#2A2926 58%); */
}

.tc {
	text-align: center;
}

.common-btn-black {
	text-align: center;
	background: var(--black);
	color: #B4A983;
}

.common-btn-black.active {
	background: radial-gradient(var(--yellow), var(--yellow-deep));
	color: var(--black);
}
</style>
