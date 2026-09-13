<template>
	<section class="gallery-panel" aria-labelledby="gallery-title">
		<div class="gallery-heading">
			<div>
				<p class="eyebrow">YOUR COLLECTION</p>
				<h2 id="gallery-title">Photo gallery</h2>
			</div>
			<span class="photo-count">{{ photos.length }} photos</span>
		</div>

		<div v-if="photos.length" class="photo-grid">
			<img v-for="(photo, index) in photos" :key="photo" :src="photo" :alt="`Captured photo ${index + 1}`">
		</div>
		<div v-else class="empty-gallery">
			<div class="empty-icon"><ion-icon :icon="imagesOutline" aria-hidden="true"></ion-icon></div>
			<h3>Your wall is still open.</h3>
			<p>Captured moments will settle here, ready to revisit.</p>
		</div>
	</section>
</template>

<script setup lang="ts">
import { IonIcon } from '@ionic/vue'
import { imagesOutline } from 'ionicons/icons'

defineProps<{
	photos: string[]
}>()
</script>

<style scoped>
.gallery-panel {
	background: #f6f3e9;
	border: 1px solid #e4e2d7;
	border-radius: 24px;
	color: #203638;
	min-height: 260px;
	padding: 24px;
}

.gallery-heading {
	align-items: flex-end;
	display: flex;
	justify-content: space-between;
	margin-bottom: 22px;
}

.eyebrow {
	color: #718477;
	font-size: 11px;
	font-weight: 700;
	letter-spacing: 0.12em;
	margin: 0 0 8px;
}

h2 {
	font-family: Georgia, 'Times New Roman', serif;
	font-size: 30px;
	font-weight: 400;
	margin: 0;
}

.photo-count {
	color: #718477;
	font-size: 12px;
}

.empty-gallery {
	align-items: center;
	border: 1px dashed #cbd3c6;
	border-radius: 16px;
	display: flex;
	flex-direction: column;
	justify-content: center;
	min-height: 170px;
	text-align: center;
}

.empty-icon {
	align-items: center;
	background: #dcece0;
	border-radius: 50%;
	color: #356258;
	display: flex;
	height: 48px;
	justify-content: center;
	margin-bottom: 12px;
	width: 48px;
}

.empty-icon ion-icon { font-size: 24px; }

h3 {
	font-family: Georgia, 'Times New Roman', serif;
	font-size: 21px;
	font-weight: 400;
	margin: 0 0 6px;
}

.empty-gallery p {
	color: #718477;
	font-size: 13px;
	margin: 0;
	max-width: 230px;
}

.photo-grid { display: grid; gap: 12px; grid-template-columns: repeat(2, 1fr); }
.photo-grid img { aspect-ratio: 1; border-radius: 12px; object-fit: cover; width: 100%; }
</style>
