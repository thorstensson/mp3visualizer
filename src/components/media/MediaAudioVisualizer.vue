<script setup lang="ts">
import { ref, onMounted, onUnmounted, inject } from "vue"
import { useEventListener } from "@vueuse/core"
import p5 from "p5"

const p5Container = ref<HTMLDivElement>()
const analyser = ref<AnalyserNode>()

let p5Instance: p5 | null = null
let audioCtx: AudioContext
let dataArray: Uint8Array
let bufferLength: number
let isPlaying = false
let audioContextInitialized = false

// Get audio element from parent component context
const audioEl = inject<{ value: HTMLAudioElement | null }>("audioEl")

/**
 * Create Web Audio API analyser for P5.js visualization
 */
const createAnalyserData = () => {
  // Check if audio element exists and is validl
  if (!audioEl?.value || !(audioEl.value instanceof HTMLMediaElement)) {
    console.warn("Audio element not available yet")
    return false
  }

  // Prevent creating multiple contexts
  if (audioContextInitialized) {
    return true
  }

  try {
    audioCtx = new AudioContext()
    const audioSrc = audioCtx.createMediaElementSource(
      audioEl.value as HTMLMediaElement
    )

    analyser.value = audioCtx.createAnalyser()
    audioSrc.connect(analyser.value)
    analyser.value.connect(audioCtx.destination)
    analyser.value.fftSize = 256 // Higher resolution for better visualization

    bufferLength = analyser.value.frequencyBinCount
    dataArray = new Uint8Array(bufferLength)

    if (audioCtx.state === "suspended") {
      audioCtx.resume()
    }

    audioContextInitialized = true
    console.log("Audio context initialized successfully")
    return true
  } catch (error) {
    console.error("Failed to create audio context:", error)
    return false
  }
}

/**
 * P5.js sketch for audio visualization
 */
const sketch = (p: p5) => {
  p.setup = () => {
    p.createCanvas(400, 400)
    p.colorMode(p.HSB, 360, 100, 100, 100)
  }

  p.draw = () => {
    p.clear() // Use clear() to make background transparent so CSS background shows

    if (isPlaying && analyser.value) {
      analyser.value.getByteFrequencyData(dataArray)

      // Calculate average amplitude for main circle size
      let sum = 0
      for (let i = 0; i < bufferLength; i++) {
        sum += dataArray[i]
      }
      const avgAmplitude = sum / bufferLength

      // Main pulsating circle
      p.push()
      p.translate(p.width / 2, p.height / 2)

      // Base circle size with audio-reactive scaling
      const baseRadius = 50
      const pulseRadius = baseRadius + (avgAmplitude / 255) * 100

      // Color based on audio intensity
      const hue = (avgAmplitude / 255) * 360

      // A common pattern in audio visualization - normalize the audio data to 0-1 (avgAmplitude / 255), then scale it to a visual range
      const saturation = 80 + (avgAmplitude / 255) * 20
      const brightness = 60 + (avgAmplitude / 255) * 40

      // Draw multiple concentric circles for depth
      for (let i = 0; i < 3; i++) {
        p.fill(hue, saturation - i * 20, brightness - i * 15, 60 - i * 20)
        p.noStroke()
        p.ellipse(0, 0, pulseRadius + i * 20, pulseRadius + i * 20)
      }

      // Draw frequency bars around the circle
      const angleStep = p.TWO_PI / bufferLength
      for (let i = 0; i < bufferLength; i++) {
        const angle = i * angleStep
        const amplitude = dataArray[i]
        const barHeight = (amplitude / 255) * 80

        const x1 = p.cos(angle) * (pulseRadius + 10)
        const y1 = p.sin(angle) * (pulseRadius + 10)
        const x2 = p.cos(angle) * (pulseRadius + 10 + barHeight)
        const y2 = p.sin(angle) * (pulseRadius + 10 + barHeight)

        p.stroke((hue + i * 2) % 360, saturation, brightness)
        p.strokeWeight(2)
        p.line(x1, y1, x2, y2)
      }

      p.pop()
    } else {
      // Static state when not playing - white border circle with no fill
      p.push()
      p.translate(p.width / 2, p.height / 2)
      p.noFill() // No fill
      p.stroke("#faf7ff") // $secondary color for border
      p.strokeWeight(4) // 4px border
      p.ellipse(0, 0, 100, 100)
      p.pop()
    }
  }
}

const startVisualization = () => {
  isPlaying = true
}

const stopVisualization = () => {
  isPlaying = false
}

onMounted(() => {
  // Create P5.js instance
  if (p5Container.value) {
    p5Instance = new p5(sketch, p5Container.value)
  }

  // Set up audio event listeners
  if (audioEl?.value) {
    audioEl.value.addEventListener("playing", startVisualization)
    audioEl.value.addEventListener("pause", stopVisualization)
    audioEl.value.addEventListener("ended", stopVisualization)
  }

  // One time event to create AudioContext when user interacts
  const cleanup = useEventListener(document, "mousedown", () => {
    cleanup()
    console.log("User clicked, attempting to create audio context")
    if (createAnalyserData()) {
      console.log("Audio context created on user interaction")
    }
  })
})

onUnmounted(() => {
  // Clean up P5.js instance
  if (p5Instance) {
    p5Instance.remove()
  }

  // Remove event listeners
  if (audioEl?.value) {
    audioEl.value.removeEventListener("playing", startVisualization)
    audioEl.value.removeEventListener("pause", stopVisualization)
    audioEl.value.removeEventListener("ended", stopVisualization)
  }
})
</script>

<template>
  <div class="p5-js" ref="p5Container"></div>
</template>

<style scoped lang="scss">
.p5-js {
  width: 400px;
  height: 400px;
  -webkit-user-select: none;
  -moz-user-select: none;
  user-select: none;
  z-index: 1;
}

:deep(.p5Canvas) {
  background-color: $primary !important;
}
</style>
