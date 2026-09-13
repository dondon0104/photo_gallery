<template>
  <ion-page>
    <ion-content :fullscreen="true">
      <main class="studio-shell">
        <header class="app-header">
          <div class="brand-mark"><ion-icon :icon="apertureOutline" aria-hidden="true"></ion-icon></div>
          <div>
            <p class="kicker">VISUAL JOURNAL</p>
            <h1>Still &amp; Seen</h1>
          </div>
          <span class="date-stamp">2026 / 09</span>
        </header>

        <section class="intro">
          <p class="kicker">A place for little things</p>
          <h2>Keep the everyday<br><em>close.</em></h2>
        </section>

        <div class="studio-grid">
          <CamComponents @capture="capturePhoto" />
          <PhotoGalleryComponents :photos="photos" />
        </div>
      </main>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import { IonContent, IonIcon, IonPage } from '@ionic/vue'
import { Camera, CameraResultType, CameraSource } from '@capacitor/camera'
import { apertureOutline } from 'ionicons/icons'
import { ref } from 'vue'
import CamComponents from '../components/CamComponents.vue'
import PhotoGalleryComponents from '../components/PhotoGalleryComponents.vue'

const photos = ref<string[]>([])

async function capturePhoto() {
  const image = await Camera.getPhoto({
    quality: 90,
    resultType: CameraResultType.DataUrl,
    source: CameraSource.Camera,
  })

  if (image.dataUrl) {
    photos.value = [...photos.value, image.dataUrl]
  }
}
</script>

<style scoped>
ion-content { --background: #e8eee8; }

.studio-shell { margin: 0 auto; max-width: 1080px; padding: 42px 28px 60px; }
.app-header { align-items: center; display: flex; gap: 13px; }
.brand-mark { align-items: center; background: #203638; border-radius: 12px; color: #a9e7c6; display: flex; height: 42px; justify-content: center; width: 42px; }
.brand-mark ion-icon { font-size: 23px; }
.kicker { color: #718477; font-size: 11px; font-weight: 700; letter-spacing: 0.14em; margin: 0 0 3px; }
.app-header h1 { color: #203638; font-family: Georgia, 'Times New Roman', serif; font-size: 22px; font-weight: 400; margin: 0; }
.date-stamp { color: #718477; font-size: 11px; margin-left: auto; }
.intro { margin: 76px 0 34px; }
.intro h2 { color: #203638; font-family: Georgia, 'Times New Roman', serif; font-size: clamp(42px, 7vw, 76px); font-weight: 400; letter-spacing: -0.02em; line-height: 0.96; margin: 10px 0 0; }
.intro em { color: #49816f; font-style: italic; }
.studio-grid { align-items: start; display: grid; gap: 24px; grid-template-columns: minmax(0, 1.05fr) minmax(0, 0.95fr); }

@media (max-width: 720px) {
  .studio-shell { padding: 28px 18px 44px; }
  .intro { margin: 54px 0 28px; }
  .studio-grid { grid-template-columns: 1fr; }
}
</style>
