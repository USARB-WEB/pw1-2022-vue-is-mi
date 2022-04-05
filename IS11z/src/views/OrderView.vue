<script>
import Pizza from "../components/Pizza.vue";
export default {
  components: {
    Pizza,
  },
  data: () => {
    return {
      selectedPizza: null,
      client: {
        name: "",
        phone: "",
        comments: "",
      },
      orderFinished: false,
    };
  },
  mounted() {
    this.selectedPizza = JSON.parse(localStorage.getItem("selectedPizza"));
  },
  methods: {
    makeOrder() {
      const order = {
        pizza: this.selectedPizza,
        client: this.client,
      };
      this.orderFinished = true;
      this.selectedPizza = null;
      localStorage.removeItem('selectedPizza')
      //alert(JSON.stringify(order))
    },
  },
};
</script>

<template>
  <main>
    <h1>Supper pizza shop</h1>

    
    <div v-if="!orderFinished">
      <h2>Selected pizza</h2>
      <template v-if="selectedPizza">
        <pizza :pizza="selectedPizza" />
        <div class="mb-3">
          <label for="exampleFormControlInput1" class="form-label">Name</label>
          <input
            type="text"
            class="form-control"
            id="exampleFormControlInput1"
            placeholder=""
            v-model="client.name"
          />
        </div>
        <div class="mb-3">
          <label for="exampleFormControlInput1" class="form-label">Phone</label>
          <input
            type="text"
            class="form-control"
            id="exampleFormControlInput1"
            placeholder="+373........"
            v-model="client.phone"
          />
        </div>
        <div class="mb-3">
          <label for="exampleFormControlTextarea1" class="form-label"
            >Comments</label
          >
          <textarea
            class="form-control"
            id="exampleFormControlTextarea1"
            rows="3"
            v-model="client.comments"
          ></textarea>
        </div>
        <button @click="makeOrder()" class="btn btn-success">Make order</button>
      </template>

      <div v-else>Please select some pizza</div>
    </div>

    <div v-if="orderFinished" class="alert alert-success" role="alert">
      Thank you for order. Please wait 15 minutes for delivery!
    </div>

    <footer>Footer</footer>
  </main>
</template>
