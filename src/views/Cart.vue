<template>
  <div>
    <NavBar />
    <br>
    <div class="carts">
      <CartForm
        v-for="cart in fetchCarts"
        :key="cart.id"
        :cart="cart"
      />
    </div>
    <button type="button" class="btn btn-info" @click.prevent="checkout">Checkout</button>
  </div>
</template>

<script>
import CartForm from '@/components/CartForm.vue'
import NavBar from '@/components/NavBar.vue'
export default {
  name: 'Carts',
  components: {
    CartForm,
    NavBar
  },
  computed: {
    fetchCarts () {
      return this.$store.state.carts
    },
    fetchProducts () {
      return this.$store.state.products
    }
  },
  methods: {
    checkout () {
      return this.$store.dispatch('checkOut')
    }
  },
  created () {
    this.$store.dispatch('fetchCarts')
  }
}
</script>

<style>
</style>
