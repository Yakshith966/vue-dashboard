<template>
  <div class="card">
    <div class="card-header pb-0 px-3">
      <h6 class="mb-0">Operations</h6>
    </div>
    <div class="col-10 text-end">
      <argon-button color="dark"  variant="gradient">
        <i class="fas fa-plus me-2"></i>
        Add
      </argon-button>
    </div>
    <div class="card-body pt-4 p-3">
      <ul class="list-group">
        <li
          class="list-group-item border-2 d-flex p-4 mb-2 bg-gray-100 border-radius-lg"
        >
          <div class="d-flex flex-column">
            <!-- <h6 class="mb-3 text-sm">Oliver Liam</h6> -->
            <span class="mb-2 text-xs">
              Title:
              <span class="text-dark font-weight-bold ms-sm-2"
                >Viking Burrito</span
              >
            </span>
            <span class="mb-2 text-xs">
              Content:
              <span class="text-dark ms-sm-2 font-weight-bold"
                >oliver@burrito.com</span
              >
            </span>
            </div>
          <div class="ms-auto text-end">
            <a
              class="btn btn-link text-danger text-gradient px-3 mb-0"
              href="javascript:;"
            >
              <i class="far fa-trash-alt me-2" aria-hidden="true"></i>Delete
            </a>
            <a class="btn btn-link text-dark px-3 mb-0" href="javascript:;">
              <i class="fas fa-pencil-alt text-dark me-2" aria-hidden="true"></i
              >Edit
            </a>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>
  
  <script>
import ArgonButton from "@/components/ArgonButton.vue";
export default {
  components: {
    ArgonButton,
  },
  name: "operations-card",
};
</script>
  