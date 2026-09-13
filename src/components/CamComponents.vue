<template>
	<section class="camera-panel" aria-labelledby="camera-title">
		<div class="panel-heading">
			<div>
				<p class="eyebrow">CAPTURE STUDIO</p>
				<h2 id="camera-title">Make a moment worth keeping.</h2>
			</div>
			<span class="status-dot" aria-label="Camera ready"></span>
		</div>

		<div class="viewfinder" aria-label="Camera preview">
			<div class="viewfinder-grid"></div>
			<span class="corner corner-top-left"></span>
			<span class="corner corner-top-right"></span>
			<span class="corner corner-bottom-left"></span>
			<span class="corner corner-bottom-right"></span>
			<div class="preview-copy">
				<ion-icon :icon="scanOutline" aria-hidden="true"></ion-icon>
				<span>Frame your shot</span>
			</div>
		</div>

		<div class="camera-controls">
			<div class="capture-note">
				<ion-icon :icon="sparklesOutline" aria-hidden="true"></ion-icon>
				<span>Ready when you are</span>
			</div>
			<ion-button class="capture-button" expand="block" @click="$emit('capture')">
				<ion-icon slot="start" :icon="cameraOutline" aria-hidden="true"></ion-icon>
				Take picture
			</ion-button>
		</div>
	</section>
</template>

<script setup lang="ts">
import { IonButton, IonIcon } from '@ionic/vue'
import { cameraOutline, scanOutline, sparklesOutline } from 'ionicons/icons'

defineEmits<{
	capture: []
}>()
</script>

<style scoped>
.camera-panel {
	background: #18292b;
	border: 1px solid rgba(196, 234, 218, 0.12);
	border-radius: 24px;
	box-shadow: 0 22px 50px rgba(9, 25, 26, 0.24);
	color: #f5f8ee;
	overflow: hidden;
	padding: 24px;
}

.panel-heading {
	align-items: flex-start;
	display: flex;
	justify-content: space-between;
	margin-bottom: 22px;
}

.eyebrow {
	color: #9dd9bb;
	font-size: 11px;
	font-weight: 700;
	letter-spacing: 0.12em;
	margin: 0 0 8px;
}

h2 {
	font-family: Georgia, 'Times New Roman', serif;
	font-size: clamp(24px, 4vw, 34px);
	font-weight: 400;
	line-height: 1.08;
	margin: 0;
	max-width: 310px;
}

.status-dot {
	background: #a9e7c6;
	border: 5px solid rgba(169, 231, 198, 0.15);
	border-radius: 50%;
	box-shadow: 0 0 0 1px rgba(169, 231, 198, 0.2);
	flex: 0 0 18px;
	height: 18px;
	margin-top: 2px;
	width: 18px;
}

.viewfinder {
	align-items: center;
	aspect-ratio: 1.35;
	background: linear-gradient(145deg, #59716a, #263e3c 58%, #142b2c);
	border-radius: 16px;
	display: flex;
	justify-content: center;
	overflow: hidden;
	position: relative;
}

.viewfinder::after {
	background: radial-gradient(circle at 62% 33%, rgba(225, 239, 199, 0.28), transparent 25%), linear-gradient(125deg, transparent 40%, rgba(190, 225, 201, 0.12));
	content: '';
	inset: 0;
	position: absolute;
}

.viewfinder-grid {
	background-image: linear-gradient(90deg, transparent 49.5%, rgba(226, 244, 224, 0.2) 50%, transparent 50.5%), linear-gradient(0deg, transparent 49.5%, rgba(226, 244, 224, 0.2) 50%, transparent 50.5%);
	inset: 18%;
	position: absolute;
}

.corner {
	border-color: rgba(238, 250, 228, 0.86);
	height: 22px;
	position: absolute;
	width: 22px;
	z-index: 1;
}

.corner-top-left { border-left: 2px solid; border-top: 2px solid; left: 18px; top: 18px; }
.corner-top-right { border-right: 2px solid; border-top: 2px solid; right: 18px; top: 18px; }
.corner-bottom-left { border-bottom: 2px solid; border-left: 2px solid; bottom: 18px; left: 18px; }
.corner-bottom-right { border-bottom: 2px solid; border-right: 2px solid; bottom: 18px; right: 18px; }

.preview-copy {
	align-items: center;
	color: rgba(245, 248, 238, 0.9);
	display: flex;
	flex-direction: column;
	font-size: 13px;
	gap: 8px;
	position: relative;
	z-index: 1;
}

.preview-copy ion-icon { font-size: 27px; }

.camera-controls { padding-top: 18px; }

.capture-note {
	align-items: center;
	color: #b5c9bd;
	display: flex;
	font-size: 12px;
	gap: 7px;
	margin-bottom: 14px;
}

.capture-note ion-icon { color: #a9e7c6; font-size: 17px; }

.capture-button {
	--background: #a9e7c6;
	--background-activated: #8fd5ad;
	--border-radius: 12px;
	--box-shadow: none;
	--color: #152d2c;
	font-weight: 700;
	margin: 0;
}

@media (max-width: 520px) {
	.camera-panel { border-radius: 20px; padding: 20px; }
}
</style>
