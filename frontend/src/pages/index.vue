<template>
  <Header />
  <div class="pt-14 bg-gray-100 min-h-screen relative z-[-2] overflow-hidden">
    <div class="w-4/5 mx-auto pt-24">
      <div>
        <h1 class="py-6">
          <span class="block mb-2 text-5xl italic tracking-wide text-green-900">
            バラバラのタスクを
          </span>
          <span class="block text-5xl italic tracking-wide text-green-900">
            1つに集約 !
          </span>
        </h1>
        <p class="italic font-semibold">
          プライベートからビジネスまで
        </p>
        <p class="italic font-semibold">
          あらゆる場面であなたのタスクを管理します。
        </p>
      </div>
      <ul class="relative left-0 top-[-60px]">
        <li 
        id="red"
        class="w-64 h-32 bg-gradient-to-l from-red-600 to-red-500 transform -skew-x-[45deg] relative z-30"></li>
        <li 
        id="green"
        class="w-64 h-32 bg-gradient-to-l from-green-600 to-green-500 transform -skew-x-[45deg] relative z-20"
        ></li>
        <li 
        id="gray"
        class="w-64 h-32 bg-gradient-to-tl from-gray-400 to-gray-300 transform -skew-x-[45deg] relative z-10"
        ></li>
      </ul>
      <div 
      id="back-gray"
      class="flex items-center absolute z-[-1] top-0 left-1/3 bg-gray-200 w-full h-full -skew-x-[25deg]"
      >
        <img id="taskImage" class="skew-x-[25deg]" :src="taskMainImage" alt="メインイメージ1" />
      </div>
      <div class="flex items-center absolute -rotate-90 bottom-14 -left-8">
        <div class="mr-4">
          <span id="scrollBar" class="block w-20 h-px rounded bg-gray-900"></span>
          <span id="scrollBall" class="absolute top-[10px] block w-2 h-2 rounded-full bg-gray-900"></span>
        </div>
        <p class="text-lg font-semibold">Scroll</p>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
import gsap from 'gsap'
import taskMainImage from '../public/task-deck_main01.png'

// ref
const isLoadingRef = ref<boolean>(false)

// elementの取得とアニメーション起動
const animationStart = () => {
  const redEl = document.getElementById('red')
  const greenEl = document.getElementById('green')
  const grayEl = document.getElementById('gray')
  const backgrayEl = document.getElementById('back-gray')
  const taskImage = document.getElementById('taskImage')
  const scrollBall = document.getElementById('scrollBall')
  
  if (isLoadingRef.value && 
    redEl && 
    greenEl && 
    grayEl && 
    backgrayEl && 
    taskImage && 
    scrollBall
    ) {
    gsap.fromTo(
      '#red', 
      { y: 195 },
      { y: 95, duration: 0.8, delay: 0.5 }
    )
    gsap.fromTo(
      '#green',
      { y: 68 },
      { y: 18, duration: 0.6, delay: 0.5 }
    )
    gsap.fromTo(
      '#gray',
      { y: -60 },
      { y: -60 }
    )
    gsap.fromTo(
      '#back-gray',
      { x: 1000, opacity: 0 },
      { x: 0, opacity: 1, duration: 1}
    )
    gsap.fromTo(
      '#taskImage',
      { opacity: 0 },
      { opacity: 1, duration: 1.5, delay: 1.5 }
    )
    gsap.fromTo(
      '#scrollBall',
      { left: 80 },
      { left: 0, duration: 1.5, repeat: -1 }
    )
  }
}

watch(() => isLoadingRef.value, () => {
  if (isLoadingRef.value) {
    animationStart()
  }
})

onMounted(() => {
  isLoadingRef.value = true
})

</script>