<template>
  <div class="bg-gray-100 mt-4 pt-6 px-8 h-48 rounded-md mx-auto flex space-x-6">
    <DieSlot v-for="die in currentDice" :key="die.id" :rolls="remainingRolls" :data="die" @hold="holdDice" />
  </div>
</template>

<script>
export default {
  name: 'DiceBox',
  props: {
    rolling: {
      type: Boolean,
      default: false
    },
    remainingRolls: {
      type: Number,
      default: 3
    }
  },
  data () {
    return {
      dice: [
        {
          id: 0,
          value: 1,
          isHeld: false,
          img: require('~/static/faces/Dice-1.svg')
        },
        {
          id: 1,
          value: 2,
          isHeld: false,
          img: require('~/static/faces/Dice-2.svg')
        },
        {
          id: 2,
          value: 3,
          isHeld: false,
          img: require('~/static/faces/Dice-3.svg')
        },
        {
          id: 3,
          value: 4,
          isHeld: false,
          img: require('~/static/faces/Dice-4.svg')
        },
        {
          id: 4,
          value: 5,
          isHeld: false,
          img: require('~/static/faces/Dice-5.svg')
        },
        {
          id: 5,
          value: 6,
          isHeld: false,
          img: require('~/static/faces/Dice-6.svg')
        }
      ],
      currentDice: [
        {
          id: 0,
          value: 1,
          isHeld: false,
          img: require('~/static/faces/Dice-1.svg')
        },
        {
          id: 1,
          value: 2,
          isHeld: false,
          img: require('~/static/faces/Dice-2.svg')
        },
        {
          id: 2,
          value: 3,
          isHeld: false,
          img: require('~/static/faces/Dice-3.svg')
        },
        {
          id: 3,
          value: 4,
          isHeld: false,
          img: require('~/static/faces/Dice-4.svg')
        },
        {
          id: 4,
          value: 5,
          isHeld: false,
          img: require('~/static/faces/Dice-5.svg')
        }
      ]
    }
  },
  watch: {
    rolling (newValue) {
      if (newValue) {
        this.rollDice()
      }
    }
  },
  methods: {
    holdDice (id) {
      this.currentDice[id].isHeld = !this.currentDice[id].isHeld
    },
    rollDice () {
      console.log('rolling dice...')
      for (let i = 0; i < this.currentDice.length; i++) {
        const elem = this.currentDice[i]
        if (!elem.isHeld) {
          const elem = this.currentDice[i]
          elem.value = Math.floor(Math.random() * 6) + 1
          elem.img = require(`~/static/faces/Dice-${elem.value}.svg`)
        }
      }
      // end roll
      this.$emit('endRoll')
      // for (let i = 0; i < this.currentDice.length; i++) {
      //   let elem = this.currentDice[i]
      //   console.log(elem)
      //   if (!elem.isHeld) {
      //     elem = this.dice[Math.floor(Math.random() * this.dice.length)]
      //   }
      // }
      /// this.dice[Math.floor(Math.random() * 6) + 1]
      // const newValue = Math.floor(Math.random() * 6) + 1
      // this.$emit('update', newValue)
    }
  }
}
</script>
