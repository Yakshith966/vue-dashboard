<template>

<div>
    <button class="slide-btn" v-on:click="BillingCards">Who we are</button>
    <button class="slide-btn" @click="OperationsCardVue">Operations</button>
  </div>

  <div class="container-fluid">
    <div class="row d-flex justify-content-center ">
      <div class="col-lg-8">
        <div class="row mt-4">
          <div class="col-xl-9 mb-xl-0 mb-4" v-if="activeComponent === 'BillingCard'">
            <BillingCard />
          </div>
          <!-- Render OperationsCardVue component when activeComponent is 'aboutUs' -->
          <div
            class="col-xl-10 mt-5 "
            v-else-if="activeComponent === 'OperationsCardVue'"
          >
            <div class="row">
              <div class="col-md-6"></div>
              <OperationsCardVue />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="row">
    <div class="col-md-7"></div>
  </div>
</template>

<script>
// import MasterCard from "@/examples/Cards/MasterCard.vue";
// import DefaultInfoCard from "@/examples/Cards/DefaultInfoCard.vue";
// import PaymentCard from "./components/PaymentCard.vue";
// import InvoiceCard from "./components/InvoiceCard.vue";
import BillingCard from "./components/BillingCard.vue";
import OperationsCardVue from "./components/OperationsCard.vue";
// import TransactionCard from "./components/TransactionCard.vue";

export default {
  name: "Billing",
  components: {
    OperationsCardVue,

    BillingCard,
  },
  data() {
    return {
      activeComponent: 'BillingCard',
      salary: {
        classIcon: "text-white fas fa-landmark",
        title: "Salary",
        desc: "Belong Interactive",
        price: "+$2000",
      },
      paypal: {
        classIcon: "text-white fab fa-paypal",
        title: "Paypal",
        desc: "Freelance Payment",
        price: "$455.00",
      },
    };
  },

  methods: {
    // Method to show the WhoWeAre component
    BillingCards() {
      this.activeComponent = "BillingCard";
      console.log("BillingCards method called");
    },
    // Method to show the AboutUs component
    OperationsCardVue() {
      this.activeComponent = "OperationsCardVue";
    },
  },
};
</script>

<style scoped>


.slide-btn {
  background-color: rgb(255, 255, 255);
  border: 2px solid #333; /* Change border color as needed */
  color: #1f1f1e; /* Change text color as needed */
  padding: 8px 13px;
  margin: 10px;
  font-size: 16px;
  border-radius: 10px;
  font-size: 14px;
  cursor: pointer;
  
  transition: background-color 0.3s, transform 0.3s;
}

.slide-btn:hover {
  background-color: #333; /* Change hover background color as needed */
  color: #fff; /* Change hover text color as needed */
  transform: translateX(5px); /* Adjust the amount of translation as needed */
}




</style>
