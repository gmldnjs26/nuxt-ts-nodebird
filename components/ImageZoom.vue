<template>
	<div id="image-zoom">
		<header>
			<h1>상세 이미지</h1>
			<v-icon id="close-btn" @click="closeModal">mdi-close</v-icon>
		</header>
		<div id="carousel-wrapper">
			<v-carousel>
				<v-carousel-item v-for="img in images" :key="img.src">
					<v-sheet>
						<v-img max-height="500" contain :src="`http://localhost:3087/${img.src}`" />
					</v-sheet>
				</v-carousel-item>
			</v-carousel>
		</div>
	</div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from 'nuxt-property-decorator';

@Component({})
export default class ImageZoom extends Vue {
	@Prop({ required: true })
	readonly images!: [];

	@Prop({ required: true })
	closeModal!: Function;
}
</script>

<style scoped>
#image-zoom {
	position: fixed;
	z-index: 5000;
	inset: 0;
}

#image-zoom header {
	height: 44px;
	background: white;
	position: relative;
	padding: 0;
	text-align: center;
}

#image-zoom header h1 {
	margin: 0;
	font-size: 17px;
	color: #333;
	line-height: 44px;
}
#close-btn {
	position: absolute;
	right: 0;
	top: 0;
	padding: 15px;
	line-height: 14px;
	cursor: pointer;
}
#carousel-wrapper {
	height: calc(100% - 44px);
	background: #090909;
}
#carousel-wrapper > div {
	height: auto !important;
}
</style>
