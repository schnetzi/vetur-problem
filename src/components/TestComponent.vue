<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
	name: 'TestComponent',
	props: {
		scenarios: {
			type: [],
			required: true,
		},
	},
	data() {
		return {
			testData: true as boolean,
		};
	},
	render() {
		return this.$scopedSlots.default({
			data: this.testData,
		});
	},
});
</script>
