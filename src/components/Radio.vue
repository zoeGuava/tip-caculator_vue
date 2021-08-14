<template>
  <input
    type="radio" 
    name="select-tip"
    class="sr-only peer" />
  <label
    class="
      w-full p-2 text-center font-bold rounded
    bg-cyan-disabled text-white
    peer-checked:bg-cyan-active peer-checked:text-cyan-darkest">
    label
  </label>
</template>

<script>
export default {
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
  }
}
</script>
