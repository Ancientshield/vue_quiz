<template>
	<div class="result">
		<div class="title">{{ results[resultIndex].title }}</div>
		<div class="desc">{{ results[resultIndex].desc }}</div>
	</div>
</template>

<script>
	export default {
		name: 'Result',
		props: ['results', 'totalCorrect'],
		computed: {
			resultIndex() {
				let index = 0;

				this.results.forEach((e, i) => {
					// e 是 results 陣列內的 item，i 是循環次數
					// 從 App.vue 陣列中即可知，index 若在 0-2 則 fail，index=3 則 pass（三題都答對）
					if (e.min <= this.totalCorrect && e.max >= this.totalCorrect) {
						index = i;
					}
				});

				return index;
			},
		},
	};
</script>

<style></style>
