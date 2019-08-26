<template>
	<div class="home">
		<img alt="Vue logo" src="../assets/logo.png" />
		<br />
		<TestComponent v-slot="{ data: myData }">
			It shows errors: {{ myData }}
		</TestComponent>
	</div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import TestComponent from '@/components/TestComponent.vue';

@Component({
	components: {
		TestComponent,
	},
})
export default class Home extends Vue {}
</script>
