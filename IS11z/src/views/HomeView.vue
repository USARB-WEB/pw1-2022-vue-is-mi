<script>
import Pizza from "../components/Pizza.vue"
export default{
  components: {
    Pizza
  },
  data: () => {
    return{
      pizzaItems: [
        {
          name: "Neapolitana",
          description: "Pizza Neapolitana description",
          price: 123,
          photo: "https://picsum.photos/id/237/200/300"
        },
        {
          name: "Diablo",
          description: "Pizza Diablo description",
          price: 222,
          photo: "https://picsum.photos/id/237/200/300"
        }
      ]
    }
  }
}
</script>

<template>
  <main>
    <h1>Supper pizza shop</h1>

    <pizza 
      v-for="pizza in pizzaItems" 
      :pizza="pizza" 
      show-buy-button 
      :key="pizza.name"
    />

    <footer>Footer</footer>
  </main>
</template>
