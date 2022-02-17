<template>
  <main>
    <div class="mx-auto max-w-7xl rounded-md shadow pt-6 pb-4 px-8 bg-white">
      <h2 class="text-lg font-semibold text-gray-700">
        Your dice:
      </h2>
      <DiceBox :rolling="isRolling" :remaining-rolls="3 - currentRoll" @endRoll="isRolling = false" />
      <div class="flex items-center h-20">
        <button type="button" class="inline-flex items-center px-4 py-2 border border-transparent text-base font-medium rounded-md text-indigo-700 bg-indigo-100 hover:bg-indigo-200 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500" @click.prevent="currentRoll = 0">
          Reset turn
        </button>
        <button type="button" class="inline-flex ml-4 items-center px-4 py-2 border border-transparent shadow-sm text-base font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500" @click.prevent="startRoll">
          <p>Roll dice</p>
          <svg xmlns="http://www.w3.org/2000/svg" class="ml-3 -mr-1 h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
            <path fill-rule="evenodd" d="M4 2a1 1 0 011 1v2.101a7.002 7.002 0 0111.601 2.566 1 1 0 11-1.885.666A5.002 5.002 0 005.999 7H9a1 1 0 010 2H4a1 1 0 01-1-1V3a1 1 0 011-1zm.008 9.057a1 1 0 011.276.61A5.002 5.002 0 0014.001 13H11a1 1 0 110-2h5a1 1 0 011 1v5a1 1 0 11-2 0v-2.101a7.002 7.002 0 01-11.601-2.566 1 1 0 01.61-1.276z" clip-rule="evenodd" />
          </svg>
        </button>
        <span class="ml-4 text-lg font-semibold text-gray-700">Rolls left: {{ 3 - currentRoll }}</span>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: 'GameWrapper',
  data () {
    return {
      isRolling: false,
      // out of 3
      currentRoll: 0,
      // out of 13
      currentTurn: 0,
      score: 0
    }
  },
  methods: {
    startRoll () {
      if (this.currentRoll < 3) {
        this.isRolling = true
        this.currentRoll++
        this.currentTurn++
        // this.score += this.currentRoll
      }
    }
  }
}
</script>
