<template>
  <div class="col-sm-6 col-md-4">
    <div class="panel panel-success">
      <div class="panel-heading">
        <h3 class="panel-title">{{stock.name}}<small>(Price: {{stock.price}} | Quantity: {{ stock.quantity}} )</small></h3>
      </div>
      <div class="panel-body">
        <div class="pull-left">
          <input v-model="quantity" type="number" class="form-control" placeholder="Quantity">
        </div>
        <div class="pull-right">
          <button :disabled="insuf || quantity <= 0" @click="sellStock" class="btn btn-success">{{insuf ? 'too much': 'sell'}}</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapActions } from 'vuex'
export default {
  props: ['stock'],
  data () {
    return {
      quantity: 0
    }
  },
  computed: {
    insuf () {
      return this.quantity > this.stock.quantity
    }
  },
  methods: {
    ...mapActions({
      sellOrder: 'sellStock'
    }),
    sellStock () {
      const order = {
        stockId: this.stock.id,
        stockPrice: this.stock.price,
        quantity: this.quantity
      }
      this.sellOrder(order)
      this.quantity = 0
    }
  }
}
</script>
