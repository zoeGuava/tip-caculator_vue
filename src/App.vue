<template>
  <main class="w-full flex flex-col items-center">
    <Header />
    <div class="w-full h-full p-8 rounded-2xl rounded-b-none bg-white">  
      <form class="space-y-10 mb-10" @reset="resetForm" @change="changeData">
        <InputField
          :input="inputData.bill"
          @update="inputUpdate"/>
        <RadioField @update="tipsUpdate" />
        <InputField 
          :input="inputData.person"
          @update="inputUpdate"/>
        <Card
          :amount="result.amount"
          :total="result.total">
          <template v-slot:resetBtn>
            <button
              @click.prevent="resetData"
              class="font-bold text-2xl text-cyan-darkest">
              RESET
            </button>
          </template>
        </Card>
      </form>
    </div>
  </main>
</template>

<script>
import Header from './components/Header.vue'
import Card from './components/Card.vue'
import InputField from './components/InputField.vue'
import RadioField from './components/RadioField.vue'

export default {
  name: 'App',
  components: {
    // HelloWorld,
    Header,
    Card,
    InputField,
    RadioField,
  },
  data() {
    return {
      inputData: {
        bill: {
          id: "bill",
          label: "Bill",
          value: 0,
        },
        person: {
          id: "person",
          label: "Person",
          value: 0,
        }
      },
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
      ],
      result: {
        amount: 0,
        total: 0
      },
    }
  },
  computed: {},
  methods: {
    tipsUpdate(target, value) {
      for(let tip of this.tips) {
        if(tip.label === 'custom') {
          tip.value = value
          tip.checked = true
          console.log('tipsUpdate value: ', value);
        } else if (tip.label === target) {
          tip.checked = true
        } else {
          tip.checked = false
        }
      }
    },
    inputUpdate(id, val){
      this.inputData[id].value = val;
    },
    changeData(){
      const bill = this.inputData.bill.value;
      const person = this.inputData.person.value;
      const tip_value = this.tips.filter(x => x.checked === true)[0].value

      const amount = bill * (tip_value / 100) / person || 0
      this.result.amount = Math.round(amount*100) / 100 || 0;
      
      const total = (bill / person) + amount || 0
      this.result.total = Math.round(total*100) / 100 || 0;
    },
    resetData() {
      this.inputData.bill.value = 0;
      this.inputData.person.value = 0;
      this.result.amount = 0;
      this.result.total = 0;
      for(let tip of this.tips) {
        if(tip.label === '5%') {
          tip.checked = true
        } else {
          if(tip.label === 'custom') { tip.value = 0 }
          tip.checked = false
        }
      }
      console.log('reset click');
      console.log('result: ' + this.formData)
    },
    resetForm() {
      console.log('reset form')
    }
  },
  mounted() {
    console.log('mounted');
  },
  beforeUpdate() {
    console.log('beforeUpdate');
  },
  updated() {
    console.log('updated');
  }
}
</script>