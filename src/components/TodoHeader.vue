<template>
	<h1>PWA 할 일 관리 앱</h1>
</template>

<style scoped>
h1 {
	color: blue;
}
</style>

<script>
export default {
	created() {
		var h1 = document.querySelector('h1');
		console.log('created', h1);
	},
	beforeMount() {
		//var h1 = document.querySelector('h1');
		//console.log('beforeMount', h1);
	},
	mounted() {
		//var h1 = document.querySelector('h1');
		//console.log('mounted', h1);
	},
};
</script>
