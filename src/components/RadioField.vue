<template>
  <fieldset className="flex flex-col">
    <legend className="font-bold text-cyan-text-light pb-2">
      Select Tip %
    </legend>
    <div className="grid grid-cols-2 gap-4">
      <div
        class="relative flex items-center text-2xl"
        :key="item.label"
        v-for="item in tips">
        <template v-if="item.label !== 'custom'">
          <input
            type="radio" 
            name="select-tip"
            :checked="item.checked"
            :id="item.label"
            @click="getCheck($event)"
            class="sr-only peer" />
          <label
            :for="item.label"
            class="
              w-full p-2 text-center font-bold rounded
            bg-cyan-disabled text-white
            peer-checked:bg-cyan-active peer-checked:text-cyan-darkest">
            {{item.label}}
          </label>
        </template>
        <span v-else>
          <label :for="item.label" class="sr-only peer"></label>
          <input
            type="number"
            min="0"
            name="select-tip"
            placeholder="Custom"
            :checked="item.checked"
            :id="item.label"
            @change="getCheck($event)"
            class="
              w-full p-2 text-right font-bold rounded
              bg-cyan-lightest text-cyan-darkest" />
        </span>
      </div>
    </div>
  </fieldset>
</template>

<script>
export default {
  name: 'RadioField',
  // props: {
  //   tip: Array,
  // },
  data() {
    return {
      tips: [
        {
          label: '5%',
          value: 5,
          checked: true
        },
        {
          label: '10%',
          value: 10,
          checked: false
        },
        {
          label: '15%',
          value: 15,
          checked: false
        },
        {
          label: '25%',
          value: 25,
          checked: false
        },
        {
          label: '50%',
          value: 50,
          checked: false
        },
        {
          label: 'custom',
          value: 0,
          checked: false
        },
      ]
    }
  },
  methods: {
    getCheck(e) {
      this.$emit('update', e.target.id, e.target.value)
    }
  }
}
</script>
