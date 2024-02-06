<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-lg-8">
        <div class="row mt-4">
          <div class="col-xl-30 mb-xl-0 mb-4">
            <billing-card />
          </div>
          <div class="col-xl-20 mt-5">
            <div class="row">
              <div class="col-md-6">

              </div>
              <OperationsCardVue />

            </div>
          </div>
        </div>

      </div>
    </div>

  </div>
  <div class="row">
    <div class="col-md-7">

    </div>

  </div>
</template>

<script>
// import MasterCard from "@/examples/Cards/MasterCard.vue";
// import DefaultInfoCard from "@/examples/Cards/DefaultInfoCard.vue";
// import PaymentCard from "./components/PaymentCard.vue";
// import InvoiceCard from "./components/InvoiceCard.vue";
import BillingCard from "./components/BillingCard.vue";
import OperationsCardVue from './components/OperationsCard.vue';
// import TransactionCard from "./components/TransactionCard.vue";

export default {
  name: "Billing",
  components: {

    OperationsCardVue,

    BillingCard,

  },
  data() {
    return {
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
};
</script>
