<template>
  <div class="card card-profile">
    <img src="../assets/img/team-2.jpg" alt="Image placeholder" class="card-img-top" />
    <div class="row justify-content-center">
      <div class="col-4 col-lg-4 order-lg-2">
        
      </div>
    </div>
    
    <div class="card-body pt-0">
      <div class="row">
        <div class="col">
          <div class="d-flex justify-content-center">
            <div class="d-grid text-center">
              <span class="text-lg font-weight-bolder">22</span>
              <span class="text-sm opacity-8">Friends</span>
            </div>
            <div class="d-grid text-center mx-4">
              <span class="text-lg font-weight-bolder">10</span>
              <span class="text-sm opacity-8">Photos</span>
            </div>
            <div class="d-grid text-center">
              <span class="text-lg font-weight-bolder">89</span>
              <span class="text-sm opacity-8">Comments</span>
            </div>
          </div>
        </div>
      </div>
      <div class="text-center mt-4">
        <h5>
          Mark Davis
          <span class="font-weight-light">, 35</span>
        </h5>
        <div class="h6 font-weight-300">
          <i class="ni location_pin mr-2"></i>Bucharest, Romania
        </div>
        <div class="h6 mt-4">
          <i class="ni business_briefcase-24 mr-2"></i>Solution Manager - Creative Tim Officer
        </div>
        <div>
          <i class="ni education_hat mr-2"></i>University of Computer Science
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// import MasterCard from "@/examples/Cards/MasterCard.vue";
// import DefaultInfoCard from "@/examples/Cards/DefaultInfoCard.vue";
// import PaymentCard from "./components/PaymentCard.vue";
// import InvoiceCard from "./components/InvoiceCard.vue";


export default {
  name: "Billing",
  components: {
    
   
    
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
