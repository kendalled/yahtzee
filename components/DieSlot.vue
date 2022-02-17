<template>
  <div>
    <p v-if="rolls === 3" class="text-center font-semibold text-gray-700 opacity-0">
      Roll
    </p>
    <img v-if="rolls === 3" draggable="false" class="w-24 h-24 bg-white rounded-xl" src="~/static/faces/Dice-0.svg">
    <div v-else>
      <p class="text-center font-semibold text-gray-700">
        {{ data.value }}
      </p>
      <img draggable="false" class="w-24 h-24 hover:opacity-75 cursor-pointer bg-white rounded-xl" :src="data.img" @click.prevent="emitHold">
      <p v-if="data.isHeld" class="text-center font-medium text-indigo-600">
        Hold
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DieSlot',
  props: {
    data: {
      type: Object,
      default () {
        return {
          id: 0,
          value: 1,
          isHeld: false,
          img: require('~/static/faces/Dice-1.svg')
        }
      }
    },
    rolls: {
      type: Number,
      default: 3
    }
  },
  methods: {
    emitHold () {
      this.$emit('hold', this.data.id)
    }
  }
}
</script>
