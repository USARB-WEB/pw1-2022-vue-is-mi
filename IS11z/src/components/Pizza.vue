<script>
export default{
    props: {
        pizza: {
            type: Object,
            required: true
        },
        showBuyButton:{
            type: Boolean,
            required: false,
            default: false
        } 
    },
    methods: {
        buyPizza(pizza){
            localStorage.setItem("selectedPizza", JSON.stringify(pizza))
            this.$router.push('/order')
        }
    }
}
</script>

<template>
    <div class="card mb-3" style="max-width: 540px">
      <div class="row g-0">
        <div class="col-md-4">
          <img
            src="https://picsum.photos/id/237/200/300"
            class="img-fluid rounded-start"
            alt="..."
          />
        </div>
        <div class="col-md-8">
          <div class="card-body">
            <h5 class="card-title">{{ pizza.name }}</h5>
            <p class="card-text">
              {{ pizza.description }}
            </p>
            <p class="card-text" v-if="showBuyButton">
              <button @click="buyPizza(pizza)" class="btn btn-info">Buy for {{ pizza.price }} MDL</button>
            </p>
          </div>
        </div>
      </div>
    </div>
</template>