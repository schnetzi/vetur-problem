<template>
	<div class="c-testcomponent">
		Testcomponent {{ isCallOfMandatoryMethodWorking(myTest) }}
	</div>
</template>

<script lang="ts">
import Vue from 'vue';
import { ITestComponent } from '@/interfaces/testComponent';

export default Vue.extend({
	name: 'TestComponent',
	props: {
		myTest: {
			type: Object as () => ITestComponent,
			required: true,
		},
		scenarios: {
			type: Array,
			required: true,
		},
		isChecked: {
			type: Boolean,
			required: true,
		},
	},
	data() {
		return {
			isCheckedChild: (this.isCallOfMethodWorking(this.myTest) ||
				this.isChecked) as boolean,
		};
	},
	computed: {
		computedMethod(): any {
			return {
				state: 'start',
			};
		},
		currentTest(): boolean {
			const state = this.computedMethod.state;
			if (state === 'start') {
				return true;
			} else {
				return false;
			}
		},
	},
	methods: {
		isCallOfMethodWorking(gameplay: ITestComponent): any {
			return (
				gameplay.Mode === 'optional' || gameplay.Mode === 'mandatory'
			);
		},
		isCallOfMandatoryMethodWorking(gameplay: ITestComponent): boolean {
			if (this.isCheckedChild) {
				console.log('yes');
			}

			return gameplay.Mode === 'mandatory';
		},
	},
});
</script>

<style lang="scss" scoped>
.c-testcomponent {
	border: 1px solid deeppink;
	padding: 20px;
}
</style>
