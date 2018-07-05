<template>
	<article class="columns" @click="onVideoSelect">
		<figure class="column is-one-quarter">
			<p class="image is-4by3">
				<img :src="thumbnailUrl">
			</p>
		</figure>
		<div class="column is-three-quarters">
			<p>
				<strong>{{ video.snippet.title }}</strong>
				<br>
				{{ video.snippet.description }}
			</p>
		</div>
	</article>
</template>

<script>
export default {
	name: 'VideoListItem',
	props: ['video'],
	computed: {
		thumbnailUrl() {
			return this.video.snippet.thumbnails.default.url;
		}
	},
	methods: {
		onVideoSelect() {
			this.$emit('videoSelect', this.video);
		}
	}
};
</script>

<style scoped>
article {
	//display: flex;
	cursor: pointer;
}

article:hover {
	background-color: #eee;
}
</style>