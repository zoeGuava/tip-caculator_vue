<template>
  <section class="rounded-xl py-8 px-6 bg-cyan-darkest">
    <ul class="flex flex-col space-y-6">
      <li class="flex flex-row justify-between items-center">
        <div>
          <h2 class="text-white">Tip Amount</h2>
          <p class="text-cyan-text-lightest">/ person</p>
        </div>
        <p class="flex flex-row text-cyan text-3xl">
          ${{amount}}
        </p>
      </li>
      <li class="flex flex-row justify-between items-center">
        <div>
          <h2 class="text-white">Total</h2>
          <p class="text-cyan-text-lightest">/ person</p>
        </div>
        <p class="flex flex-row text-cyan text-3xl">
          ${{total}}
        </p>
      </li>
      <li class="w-full py-2 flex flex-row justify-center items-center bg-cyan rounded-sm">
        <slot name="resetBtn"></slot>
      </li>
    </ul>
  </section>
</template>

<script>

export default {
  props: {
    amount: Number,
    total: Number,
  },
  components: {
  },
  name: 'Card',
  methods: {
  }
}
</script>
