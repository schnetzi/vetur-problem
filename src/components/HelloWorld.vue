<template>
	<div class="hello">
		<TestComponent
			:my-test="myTest"
			:scenarios="scenarios"
			:is-checked="true"
		></TestComponent>
	</div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import TestComponent from './TestComponent.vue';
import { ITestComponent } from '@/interfaces/testComponent';

@Component({
	components: {
		TestComponent,
	},
})
export default class HelloWorld extends Vue {
	@Prop() private msg!: string;

	get myTest(): ITestComponent {
		return {
			TestId: '1',
			Mode: 'optional',
		};
	}

	get scenarios(): string[] {
		return [];
	}
}
</script>

<style scoped lang="scss">
h3 {
	margin: 40px 0 0;
}
ul {
	list-style-type: none;
	padding: 0;
}
li {
	display: inline-block;
	margin: 0 10px;
}
a {
	color: #42b983;
}
</style>
