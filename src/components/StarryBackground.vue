<script setup>
import { ref, onMounted } from 'vue'

const stars = ref([])
const meteors = ref([])

onMounted(() => {
  // ✨ Generate tiny stars
  stars.value = Array.from({ length: 180 }).map((_, i) => ({
    id: i,
    x: Math.random() * 100,
    y: Math.random() * 100,
    size: Math.random() * 1.2 + 0.4,
    opacity: Math.random() * 0.8 + 0.2,
  }))

  // 🌠 Shooting stars loop
  setInterval(() => {
    const id = crypto.randomUUID()
    meteors.value.push({
      id,
      x: Math.random() * 80 + 10,
      y: Math.random() * 40 + 10,
      dur: Math.random() * 1.5 + 1.5,
    })
    if (meteors.value.length > 6) meteors.value.shift()
  }, 2500)
})
</script>

<template>
  <div class="absolute inset-0 overflow-hidden bg-gradient-to-b from-black via-[#0f172a] to-black">
    
    <!-- 🌌 Nebula / Galaxy glow -->
    <div class="absolute left-1/2 top-1/2 w-[160%] h-[160%] 
                -translate-x-1/2 -translate-y-1/2
                bg-[radial-gradient(circle,rgba(59,130,246,0.25),rgba(168,85,247,0.2),transparent_70%)]
                blur-3xl opacity-60 animate-pulse">
    </div>

    <!-- ✨ Stars -->
    <div v-for="s in stars" :key="s.id"
         class="absolute rounded-full bg-white"
         :style="{
           left: s.x + '%',
           top: s.y + '%',
           width: s.size + 'px',
           height: s.size + 'px',
           opacity: s.opacity,
           animation: `twinkle ${2 + Math.random()*3}s infinite`
         }">
    </div>

    <!-- 🌠 Shooting stars -->
    <div v-for="m in meteors" :key="m.id"
         class="absolute"
         :style="{ left: m.x + '%', top: m.y + '%', animation: `meteor ${m.dur}s linear 1` }">
      <div class="h-[2px] w-32 bg-white rounded-full blur-[2px] shadow-[0_0_16px_rgba(255,255,255,1)]"/>
    </div>
  </div>
</template>

<style scoped>
@keyframes twinkle {
  0%,100% { opacity: 0.3 }
  50% { opacity: 1 }
}

@keyframes meteor {
  0%   { transform: translate(0,0) rotate(-25deg); opacity:0 }
  10%  { opacity:1 }
  100% { transform: translate(-70vw, 60vh) rotate(-25deg); opacity:0 }
}
</style>
