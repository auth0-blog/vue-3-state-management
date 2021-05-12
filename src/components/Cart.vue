<template>
  <div class="card">
    <div class="card-body">
      <h5 class="card-title">Your Cart</h5>
    </div>
    <ul class="list-group list-group-flush">
      <li
        class="list-group-item d-flex justify-content-between align-items-center"
      >
        An item
        <span class="badge badge-primary badge-pill">1</span>
      </li>
      <li
        class="list-group-item d-flex justify-content-between align-items-center"
      >
        A second item
        <span class="badge badge-primary badge-pill">1</span>
      </li>
      <li
        class="list-group-item d-flex justify-content-between align-items-center"
      >
        A third item
        <span class="badge badge-primary badge-pill">1</span>
      </li>
    </ul>

    <div class="card-body">
      <router-link to="/shop" class="btn btn-primary btn-block"
        >Checkout</router-link
      >
    </div>
  </div>
</template>

<script>
export default {};
</script>
