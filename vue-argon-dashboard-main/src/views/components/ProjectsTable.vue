<template>
  <div class="card mb-4">
    <div class="card-header pb-0">
      <h6>Carousel Images</h6>
    </div>
    <div class="card-body pt-4 p-3">
      <ul class="list-group">
        <li
          class="list-group-item border-0 d-flex p-4 mb-2 bg-gray-100 border-radius-lg"
        >
          <div class="d-flex flex-column">
            <h6 class="mb-3 text-sm">Oliver Liam</h6>
            <img
              src="../../assets/img/bg-profile.jpg"
              alt="Image placeholder"
              class="card-img-top pt-4 w-40 border-radius-lg"
            />
          </div>
          <div class="ms-auto text-end pt-8">
            <a
              class="btn btn-link text-danger text-gradient px-3 mb-0"
              href="javascript:;"
            >
              <i class="far fa-trash-alt me-2" aria-hidden="true"></i>Delete
            </a>
          </div>
        </li>
      </ul>
    </div>
  </div>

  <div class="card shadow-lg mt-3">
    <div class="card-header pb-0">
      <h6>Gallery Images</h6>
    </div>

    <div class="card-body p-3">
      <div class="row gx-4">
        <div class="col-auto">
          <div class="avatar avatar-xl position-relative">
            <img
              src="../../assets/img/bg-profile.jpg"
              alt="profile_image"
              class="shadow-sm w-100 border-radius-lg"
            />
          </div>
        </div>
        <div class="col-auto my-auto">
          <div class="h-100">
            <h5 class="mb-1">Sayo Kravits</h5>
            <p class="mb-0 font-weight-bold text-sm">Public Relations</p>
          </div>
        </div>
        <div
          class="mx-auto mt-3 col-lg-4 col-md-6 my-sm-auto ms-sm-auto me-sm-0"
        >
          <a
            class="btn btn-link text-danger text-gradient px-10 mb-0"
            href="javascript:;"
          >
            <i class="far fa-trash-alt me-2" aria-hidden="true"></i>Delete
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "projects-table",
};
</script>
