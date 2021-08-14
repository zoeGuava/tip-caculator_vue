<template>
  <div class="flex flex-col space-y-2">
    <div class="font-bold text-base text-cyan-text-light">
      <label :htmlFor="input.id">{{input.label}}</label>
    </div>
    <div class="relative flex flex-row">
      <IconDollar v-show="input.id === 'bill'" class="absolute h-full p-4 text-cyan-text-lightest" />
      <IconPerson v-show="input.id === 'person'" class="absolute h-full p-4 text-cyan-text-lightest" />
      <input
        type="number"
        min="0"
        v-model.number="value"
        :name="input.label"
        :id="input.id"
        v-on:input="updateText"
        class="
          w-full h-full py-2 px-4
          outline-none bg-cyan-lightest rounded 
          text-2xl font-bold text-right"
      />
    </div>
  </div>
</template>

<script>
import IconDollar from './Icons/Dollar.vue'
import IconPerson from './Icons/Person.vue'

export default {
  name: 'InputField',
  components: {
    IconDollar,
    IconPerson
  },
  props: {
    input: Object
  },
  data() {
    return {
      id: this.input.id,
      value: this.input.value
    }
  },
  methods: {
    // clear(e) {
    //   if(e.target.value === 0) {
    //     console.log(e.target.value)
    //     return e.target.value = '';
    //   }
    //   console.log(e.target.value)
    // },
    updateText() {
      this.$emit('update', this.input.id, this.value);
    }
  }
}
</script>
