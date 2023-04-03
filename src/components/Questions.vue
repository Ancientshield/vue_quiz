<template>
	<div class="questions-ctr">
		<div class="progress">
			<div
				class="bar"
				:style="{ width: `${(questionsAnswered / questions.length) * 100}%` }"
			></div>
			<div class="status">
				{{ questionsAnswered }} out of {{ questions.length }} questions answered
			</div>
		</div>
		<!-- qi 是 question index 縮寫，由 v-for 回圈自動產生 跟 questions 無關 -->
		<div
			class="single-question"
			v-for="(question, qi) in questions"
			:key="question.q"
			v-show="questionsAnswered === qi"
		>
			<div class="question">{{ question.q }}</div>
			<div class="answers">
				<!-- answer.is_correct 是 App.vue Array 內的一個值 -->
				<div
					class="answer"
					v-for="answer in question.answers"
					key="answer.text"
					@click.pervent="selectAnswer(answer.is_correct)"
				>
					{{ answer.text }}
				</div>
			</div>
		</div>
	</div>
</template>

<script>
	export default {
		name: 'Questions',
		props: ['questions', 'questionsAnswered'],
		emits: ['question-answered'],
		methods: {
			selectAnswer(is_correct) {
				this.$emit('question-answered', is_correct);
			},
		},
	};
</script>

<style></style>
