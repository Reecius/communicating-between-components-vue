<template>
	<div class="component">
		<h3>You may edit the User here</h3>
		<p>Edit me!</p>
		<p>User Age: {{ userAge }}</p>
		<button @click="editAge">Edit Age</button>
		<button @click="editAgeFn()">Edit Age From User Function</button>
		<button @click="editAgeWithEventBus">Edit Age With Event Bus</button>
		<button @click="editAgeWithEventBusMethod">Edit Age Wiith Event Bus Method</button>
	</div>
</template>

<script>
	import { eventBus } from '../main';

	export default {
		props: ['userAge', 'editAgeFn'],
		methods: {
			editAge() {
				this.userAge = 30;
				this.$emit('ageWasEdited', this.userAge);
			},
			editAgeWithEventBus() {
				this.userAge = 30;
				eventBus.$emit('ageWasEditedWithEventBus', this.userAge);
			},
			editAgeWithEventBusMethod() {
				this.userAge = 30;
				eventBus.changeAge(this.userAge);
			}
		}
	};
</script>

<style scoped>
	div {
		background-color: lightgreen;
	}
</style>
