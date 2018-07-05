<template>
	<div class="container">
		<div class="field has-addons">
			<div class="control has-icons-left">
				<input @input="onInput" class="input is-large" placeholder="Search Videos" />
				<span class="icon is-medium is-left">
					<i class="fas fa-video"></i>
				</span>
			</div>
			<div class="control">
				<a class="button is-info is-large">
					Search
				</a>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: 'SearchBar',
	methods: {
		onInput(event) {
			this.$emit('termChange', event.target.value);
		}
	}
};
</script>

<style scoped>
.container {
	padding-bottom: 40px;
}

.field.has-addons {
	justify-content: center;
}
</style>