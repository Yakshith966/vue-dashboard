
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
    </div>

    <div class="card-body pt-3 p-3 w-100">
      <div
        v-if="loading == true"
        style="justify-content: center; display: flex"
      >
        <LoadingBar />
      </div>

      <ul
        v-else
        class="list-group d-flex flex-row flex-wrap gap-5 w-100 justify-content-center m-auto"
      >
        <li
          v-for="(item, index) in items"
          :key="index"
          class="list-group-item border-0 d-flex flex-column justify-content-between col-md-3 mb-3 bg-gray-100 border-radius-lg"
        >
          <!-- <div> -->
          <div class="d-flex flex-column">
            <h6 class="mb-3 text-sm">Gallery Images</h6>
            <img
              :src="basePath + item.image_path"
              alt="Image placeholder"
              class="card-img-top w-100 border-radius-lg"
            />
          </div>
          <div class="ms-auto pt-2 pb--3 d-flex">
            <a
              class="btn btn-link text-danger text-gradient px-3"
              href="javascript:;"
              data-toggle="modal"
              data-target="#confirmDeleteModal1"
              @click="selectedAppDataItems=item"
            >
              <i class="far fa-trash-alt me-2" aria-hidden="true"></i>Delete
            </a>
          </div>
          <div
            class="modal"
            id="confirmDeleteModal1"
            tabindex="-1"
            role="dialog"
          >
            <div class="modal-dialog" role="document">
              <div class="modal-content">
                <div class="modal-header">
                  <h5 class="modal-title">Confirm Deletion</h5>
                  <button
                    type="button"
                    class="close"
                    data-dismiss="modal"
                    aria-label="Close"
                    :id="'closeModal2' + selectedAppDataItems.id"
                  >
                    <span aria-hidden="true">&times;</span>
                  </button>
                </div>
                <div class="modal-body">
                  Are you sure you want to delete this record?
                </div>
                <div class="modal-footer">
                  <button
                    type="button"
                    class="btn btn-secondary"
                    data-dismiss="modal"
                  >
                    Cancel
                  </button>
                  <button
                    type="button"
                    class="btn btn-danger"
                    @click="deleteRecord()"
                  >
                    Delete
                  </button>
                </div>
              </div>
            </div>
          </div>
          <!-- </div> -->
          <div
            class="modal fade"
            id="galleryImages"
            tabindex="-1"
            role="dialog"
            aria-labelledby="exampleModalLabel"
            aria-hidden="true"
            @click="selectedAppData = item"
          >
            <div class="modal-dialog" role="document">
              <div class="modal-content">
                <div class="modal-header">
                  <h5 class="modal-title" id="exampleModalLabel">
                    Gallery Images
                  </h5>
                  <button
                    type="button"
                    class="close"
                    data-dismiss="modal"
                    aria-label="Close"
                    ref="imgDeleteBtn"
                    style="border: none"
                    :id="'closeModal' + item.id"
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
                    :id="'closeModal' + item.id"
                  >
                    Close
                  </button>
                  <button
                    type="button"
                    class="btn btn-primary"
                    @click="submitForm('1')"
                  >
                    Upload Image
                  </button>
                </div>
              </div>
            </div>
          </div>
        </li>
      </ul>
    </div>
  </div>
  <div class="card shadow-lg mt-3">
    
    <div class="card-header pb-0">
      <h6>Carousel Images</h6>
      <div class="col-5 w-95 text-end mb-4">
        <argon-button
          color="dark"
          variant="gradient"
          data-toggle="modal"
          data-target="#carouselImages"
        >
          <i class="fas fa-plus me-2"></i>
          Add
        </argon-button>
      </div>
    </div>
    <div v-if="loading == true" style="justify-content: center; display: flex">
      <LoadingBar />
    </div>

    <div v-else  >
      <!-- Iterate over data with section_id 2 -->
      <div v-for="(item, index) in itemscarousel" :key="index">
        <div
          class="card-body p-3 d-flex align-items-center justify-content-between" 
        >
          <img
            :src="basePath + item.image_path"
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
          class="modal fade"
          id="carouselImages"
          tabindex="-1"
          role="dialog"
          aria-labelledby="exampleModalLabel"
          aria-hidden="true"
          @click="selectedAppData = item"
        >
          <div class="modal-dialog" role="document">
            <div class="modal-content">
              <div class="modal-header">
                <h5 class="modal-title" id="exampleModalLabel">
                  Carousel Images
                </h5>
                <button
                  type="button"
                  class="close"
                  data-dismiss="modal"
                  aria-label="Close"
                  ref="imgDeleteBtn"
                  style="border: none"
                  :id="'closeModal' + item.id"
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
                  :id="'closeModal' + item.id"
                >
                  Close
                </button>
                <button
                  type="button"
                  class="btn btn-primary"
                  @click="submitForm('2')"
                >
                  Upload Image
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
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
    LoadingBar,
  },
  data() {
    return {
      image: null,
      // section_id: 1,
      selectedAppData: "",
      loading: false,
      items: [],
      selectedAppDataItems:"",
      itemscarousel: [],
      basePath: "http://demo.localhost:8000/storage/images/",
    };
  },
  name: "projects-table",
  mounted() {
    this.fetchData();
    this.fetchCarousel();
  },
  methods: {
    iamalive(items)
    {
        this.selectedAppDataItems=items;
        console.log(this.selectedAppDataItems.id);
        
    },
    handleImageChange(event) {
      // Update image data when a file is selected
      this.image = event.target.files[0];
      // this.selectedImageSrc = URL.createObjectURL(this.selectedImage);
    },
    clearForm() {
      this.image = null;
      console.log(this.image);
      // this.selectedAppData = "";
    },
    async submitForm(section_id) {
      try {
        const formData = new FormData();
        // Append your form data including the image
        formData.append("section_id", section_id);
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

        // this.$refs.imgDeleteBtn.click();
        document
          .getElementById("closeModal" + this.selectedAppData.id)
          .click();
        if (section_id === "1") {
          this.fetchData();
          console.log("yakshi" + this.selectedAppData.id);
        } else if (section_id === "2") {
          this.fetchCarousel();
        }
        console.log("Response:", response.data);
        this.selectedAppData = "";
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
    async fetchCarousel() {
      this.loading = true;
      try {
        await axios
          .get(`http://localhost:8000/api/media/2`)
          .then((result) => {
            this.itemscarousel = result.data.data;
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
     async deleteRecord() {
      try {
        const response = await axios.delete(
          `http://localhost:8000/api/media/${this.selectedAppDataItems.id}`
        );
        console.log(response);

        if (response.status === 200) {
          document
            .getElementById("closeModal2" + this.selectedAppDataItems.id)
            .click();
            
        
          // this.$refs.closeDeleteBtn.click();
          this.fetchData();
          this.selectedAppDataItems = "";
        } else {
          // this.$snotify.success('Something went wrong');
        }
      } catch (error) {
        console.log(error);
        // alert("Something went wrong");
      }
  
    },
  },
};
</script>