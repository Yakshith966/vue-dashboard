<template>
    <!-- Modal -->
    <div class="modal fade" id="exampleModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel"
        aria-hidden="true">
        <div class="modal-dialog" role="document">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="exampleModalLabel">News</h5>
                    <button type="button" class="close" data-dismiss="modal" aria-label="Close" style="border: none;">
                        <span aria-hidden="true">&times;</span>
                    </button>
                </div>
                <div class="modal-body">
                    <form @submit.prevent="submitForm">
                        <div class="mb-3">
                            <label for="imageInput" class="form-label">Image</label>
                            <input type="file" class="form-control" id="imageInput" accept="image/*">
                        </div>
                        <div class="mb-3">
                            <label for="titleInput" class="form-label">Title</label>
                            <input type="text" class="form-control" id="titleInput" v-model="title">
                        </div>
                        <div class="mb-3">
                            <label for="contentInput" class="form-label">Content</label>
                            <textarea class="form-control" id="contentInput" rows="3" v-model="content"></textarea>
                        </div>
                    </form>

                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
                    <button type="button" class="btn btn-primary">Save changes</button>
                </div>
            </div>
        </div>
    </div>



    <div class="card m-4">
        <div class="card-header pb-0">
            <h6>Product Images</h6>
            <div class="col-5 w-95 text-end mb-4">
                <argon-button color="dark" variant="gradient" data-toggle="modal" data-target="#exampleModal">
                    <i class="fas fa-plus me-2"></i>
                    Add
                </argon-button>
            </div>
        </div>
        <div class="card-body pt-3 w-100">
            <ul class="list-group d-flex flex-row flex-wrap gap-5 w-100 justify-content-center m-auto">
                <li class="list-group-item border-0 d-flex flex-column col-md-3 mb-3 bg-gray-100 border-radius-lg">
                    <div class="d-flex flex-column align-items-center">
                        <img src="../../assets/img/bg-profile.jpg" alt="Image placeholder"
                            class="card-img-top pt-0 mt-2 w-100 border-radius-lg" />
                        <h6 class="mb-3 pt-3">Title</h6>
                        <p class="mb-3 text-sm">Content goes here enter the content related to this image cdhsvcgsvcac
                            dc adcvgvg</p>
                    </div>
                    <div class="ms-auto  pt-2 pb-0 d-flex">
                        <a class="btn btn-link text-dark text-gradient px-3" href="javascript:;" data-toggle="modal"
                            data-target="#exampleModal">
                            <i class="fas fa-pencil-alt text-dark me-2" aria-hidden="true"></i>Edit
                        </a>
                        <a class="btn btn-link text-danger text-gradient px-4" href="javascript:;">
                            <i class="far fa-trash-alt me-2" aria-hidden="true"></i>Delete
                        </a>
                    </div>
                </li>
                <li class="list-group-item border-0 d-flex flex-column col-md-3 mb-3 bg-gray-100 border-radius-lg">
                    <div class="d-flex flex-column align-items-center">
                        <img src="../../assets/img/bg-profile.jpg" alt="Image placeholder"
                            class="card-img-top pt-0 mt-2 w-100 border-radius-lg" />
                        <h6 class="mb-3 pt-3">Title</h6>
                        <p class="mb-3 text-sm">Content goes here enter the content related to this image cdhsvcgsvcac
                            dc adcvgvg</p>
                    </div>
                    <div class="ms-auto  pt-2 pb-0 d-flex">
                        <a class="btn btn-link text-dark text-gradient px-3" href="javascript:;">
                            <i class="fas fa-pencil-alt text-dark me-2" aria-hidden="true"></i>Edit
                        </a>
                        <a class="btn btn-link text-danger text-gradient px-4" href="javascript:;">
                            <i class="far fa-trash-alt me-2" aria-hidden="true"></i>Delete
                        </a>
                    </div>
                </li>
                <li class="list-group-item border-0 d-flex flex-column col-md-3 mb-3 bg-gray-100 border-radius-lg">
                    <div class="d-flex flex-column align-items-center">
                        <img src="../../assets/img/bg-profile.jpg" alt="Image placeholder"
                            class="card-img-top pt-0 mt-2 w-100 border-radius-lg" />
                        <h6 class="mb-3 pt-3">Title</h6>
                        <p class="mb-3 text-sm">Content goes here enter the content related to this image cdhsvcgsvcac
                            dc adcvgvg</p>
                    </div>
                    <div class="ms-auto  pt-2 pb-0 d-flex">
                        <a class="btn btn-link text-dark text-gradient px-3" href="javascript:;">
                            <i class="fas fa-pencil-alt text-dark me-2" aria-hidden="true"></i>Edit
                        </a>
                        <a class="btn btn-link text-danger text-gradient px-4" href="javascript:;">
                            <i class="far fa-trash-alt me-2" aria-hidden="true"></i>Delete
                        </a>
                    </div>
                </li>
                <li class="list-group-item border-0 d-flex flex-column col-md-3 mb-3 bg-gray-100 border-radius-lg">
                    <div class="d-flex flex-column align-items-center">
                        <img src="../../assets/img/bg-profile.jpg" alt="Image placeholder"
                            class="card-img-top pt-0 mt-2 w-100 border-radius-lg" />
                        <h6 class="mb-3 pt-3">Title</h6>
                        <p class="mb-3 text-sm">Content goes here enter the content related to this image cdhsvcgsvcac
                            dc adcvgvg</p>
                    </div>
                    <div class="ms-auto  pt-2 pb-0 d-flex">
                        <a class="btn btn-link text-dark text-gradient px-3" href="javascript:;">
                            <i class="fas fa-pencil-alt text-dark me-2" aria-hidden="true"></i>Edit
                        </a>
                        <a class="btn btn-link text-danger text-gradient px-4" href="javascript:;">
                            <i class="far fa-trash-alt me-2" aria-hidden="true"></i>Delete
                        </a>
                    </div>
                </li>
                <li class="list-group-item border-0 d-flex flex-column col-md-3 mb-3 bg-gray-100 border-radius-lg">
                    <div class="d-flex flex-column align-items-center">
                        <img src="../../assets/img/bg-profile.jpg" alt="Image placeholder"
                            class="card-img-top pt-0 mt-2 w-100 border-radius-lg" />
                        <h6 class="mb-3 pt-3">Title</h6>
                        <p class="mb-3 text-sm">Content goes here enter the content related to this image cdhsvcgsvcac
                            dc adcvgvg</p>
                    </div>
                    <div class="ms-auto  pt-2 pb-0 d-flex">
                        <a class="btn btn-link text-dark text-gradient px-3" href="javascript:;">
                            <i class="fas fa-pencil-alt text-dark me-2" aria-hidden="true"></i>Edit
                        </a>
                        <a class="btn btn-link text-danger text-gradient px-4" href="javascript:;">
                            <i class="far fa-trash-alt me-2" aria-hidden="true"></i>Delete
                        </a>
                    </div>
                </li>
                <li class="list-group-item border-0 d-flex flex-column col-md-3 mb-3 bg-gray-100 border-radius-lg">
                    <div class="d-flex flex-column align-items-center">
                        <img src="../../assets/img/bg-profile.jpg" alt="Image placeholder"
                            class="card-img-top pt-0 mt-2 w-100 border-radius-lg" />
                        <h6 class="mb-3 pt-3">Title</h6>
                        <p class="mb-3 text-sm">Content goes here enter the content related to this image cdhsvcgsvcac
                            dc adcvgvg</p>
                    </div>
                    <div class="ms-auto  pt-2 pb-0 d-flex">
                        <a class="btn btn-link text-dark text-gradient px-3" href="javascript:;">
                            <i class="fas fa-pencil-alt text-dark me-2" aria-hidden="true"></i>Edit
                        </a>
                        <a class="btn btn-link text-danger text-gradient px-4" href="javascript:;">
                            <i class="far fa-trash-alt me-2" aria-hidden="true"></i>Delete
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
    name: "products-table",
    components: {
        ArgonButton
    }
}
</script>