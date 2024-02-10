
<template>
  <div class="card mb-4">
    <div class="card-header pb-0">
      <h6>Gallery Images</h6>
      <div class="col-5 w-95 text-end mb-4">
        <argon-button
          color="dark"
          variant="gradient"
          data-toggle="modal"
          data-target="#galleryImages"
          @click="clearForm"
        >
          <i class="fas fa-plus me-2"></i>
          Add
        </argon-button>
      </div>
      
      <div
        class="modal fade"
        id="galleryImages"
        tabindex="-1"
        role="dialog"
        aria-labelledby="exampleModalLabel"
        aria-hidden="true"
      >
        <div class="modal-dialog" role="document">
         
          <div class="modal-content">
            <div class="modal-header">
              <h5 class="modal-title" id="exampleModalLabel">Gallery Images</h5>
              <button
                type="button"
                class="close"
                data-dismiss="modal"
                aria-label="Close"
                ref="imgDeleteBtn"
              >
                <span aria-hidden="true">&times;</span>
              </button>
            </div>
            <div class="modal-body">
              <form @submit.prevent="submitForm">
                <div class="mb-3">
                  <label for="imageInput" class="form-label">Image</label>
                  <input
                    type="file"
                    class="form-control"
                    id="imageInput"
                    @change="handleImageChange"
                    accept="image/*"
                  />
                </div>
              </form>
            </div>
            <div class="modal-footer">
              <button
                type="button"
                class="btn btn-secondary"
                data-dismiss="modal"
                ref="imgDeleteBtn"
              >
                Close
              </button>
              <button type="button" class="btn btn-primary" @click="submitForm">
                Upload Image
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
   
    <div class="card-body pt-3 p-3 w-100">
      <div v-if="loading == true" style="justify-content: center; display: flex;">
            <LoadingBar />
          </div>  
      
  <ul  v-else class="list-group d-flex flex-row flex-wrap gap-5 w-100 justify-content-center m-auto">
   
    <li  v-for="(item, index) in items" :key="index" class="list-group-item border-0 d-flex flex-column col-md-3 mb-3 bg-gray-100 border-radius-lg">
      <div class="d-flex flex-column">
        <h6 class="mb-3 text-sm">Gallery Images</h6>
        <img :src="basePath + item.image_path" alt="Image placeholder" class="card-img-top w-100 border-radius-lg" />
      </div>
      <div class="ms-auto pt-2 pb--3">
        <a class="btn btn-link text-danger text-gradient px-3" href="javascript:;">
          <i class="far fa-trash-alt me-2" aria-hidden="true"></i>Delete
        </a>
      </div>
    </li>
  </ul>
</div>
  </div>
  <div class="card shadow-lg mt-3">
    <div class="card-header pb-0">
      <h6>Carousel Images</h6>
      <div class="col-5 w-95 text-end mb-4">
        <argon-button color="dark" variant="gradient">
          <i class="fas fa-plus me-2"></i>
          Add
        </argon-button>
      </div>
    </div>
    <div
      class="card-body p-3 d-flex align-items-center justify-content-between"
    >
      <img
        src="../../assets/img/bg-profile.jpg"
        alt="profile_image"
        class="shadow-sm border-radius-lg w-15"
      />

      <a
        class="btn btn-link text-danger text-gradient px-20 m-0"
        href="javascript:;"
      >
        <i class="far fa-trash-alt me-2" aria-hidden="true"></i>Delete
      </a>
    </div>
    <div
      class="card-body p-3 d-flex align-items-center justify-content-between"
    >
      <img
        src="../../assets/img/bg-profile.jpg"
        alt="profile_image"
        class="shadow-sm border-radius-lg w-15"
      />

      <a
        class="btn btn-link text-danger text-gradient px-20 m-0"
        href="javascript:;"
      >
        <i class="far fa-trash-alt me-2" aria-hidden="true"></i>Delete
      </a>
    </div>
  </div>
</template>
<script>
import ArgonButton from "@/components/ArgonButton.vue";
import LoadingBar from "../components/LoadingBar.vue";
import axios from "axios";
export default {
  components: {
    ArgonButton,
    LoadingBar
    
  },
  data() {
    return {
      image: null,
      section_id: 1,
      loading:false,
      items: [],
      basePath: "http://demo.localhost:8000/storage/images/",
    };
  },
  name: "projects-table",
  mounted()
  {
    this.fetchData();
  },
  methods: {
    handleImageChange(event) {
      // Update image data when a file is selected
      this.image = event.target.files[0];
      // this.selectedImageSrc = URL.createObjectURL(this.selectedImage);
    },
    clearForm()
    {
      this.image=null;
      console.log(this.image);
    },
    async submitForm() {
      try {
        const formData = new FormData();
        // Append your form data including the image
        formData.append("section_id", this.section_id);
        formData.append("image_path", this.image);
        const response = await axios.post(
          "http://localhost:8000/api/media",
          formData,
          {
            headers: {
              "Content-Type": "multipart/form-data",
            },
          }
        );
        
        this.$refs.imgDeleteBtn.click();
        this.fetchData();
        console.log("Response:", response.data);
        // Handle response data as needed
      } catch (error) {
        console.error("Error:", error);
        // Handle error
      }
    },
    async fetchData() {
      this.loading = true;
      try {
        
        await axios
          .get(`http://localhost:8000/api/media/1`)
          .then((result) => {
            this.items = result.data.data;
            setTimeout(() => {
              this.loading = false;
              console.log(this.loading);
              
            }, 1000);
          })
          .catch((err) => {
            console.log(err);
            this.loading = false;
          });
      } catch (error) {
        console.error("Error fetching data:", error);
      }
    },
  },
};
</script>