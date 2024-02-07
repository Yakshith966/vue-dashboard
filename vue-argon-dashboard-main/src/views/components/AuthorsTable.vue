<template >
  <div class="card">
    <div class="card-header pb-0">
      <h6>Homepage</h6>
      <div>
        <div class="col-5 w-95 text-end mb-4">
          <argon-button
            color="dark"
            variant="gradient"
            @click="openModalAndFetchData"
            data-toggle="modal"
            data-target="#exampleModal"
          >
            <i class="fas fa-plus me-2"></i>
            Add
          </argon-button>
        </div>
        <class
          class="modal fade"
          id="exampleModal"
          tabindex="-1"
          role="dialog"
          aria-labelledby="exampleModalLabel"
          aria-hidden="true"
        >
          <div class="modal-dialog" role="document">
            <div class="modal-content">
              <div class="modal-header">
                <h5 class="modal-title" id="exampleModalLabel">Homepage</h5>
                <button
                  type="button"
                  class="close"
                  data-dismiss="modal"
                  aria-label="Close"
                  style="border: none"
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
                  <div class="mb-3">
                    <label for="titleInput" class="form-label">Title</label>
                    <div v-if="!title" class="text-danger">
                      {{ errorMessage.title }}
                    </div>
                    <input
                      type="text"
                      class="form-control"
                      id="titleInput"
                      v-model="title"
                    />
                  </div>
                  <div class="mb-3">
                    <label for="contentInput" class="form-label">Content</label>
                    <textarea
                      class="form-control"
                      id="contentInput"
                      rows="3"
                      v-model="content"
                    ></textarea>
                    <div v-if="!content" class="text-danger">
                      {{ errorMessage.content }}
                    </div>
                  </div>
                </form>
              </div>
              <div class="modal-footer">
                <button
                  type="button"
                  class="btn btn-secondary"
                  data-dismiss="modal"
                >
                  Close
                </button>
                <button
                  type="button"
                  class="btn btn-primary"
                  @click="submitForm"
                  
                >
                <!-- :data-dismiss="errorMessage.title!='' && errorMessage.content!='' ? 'modal' : null"  -->
                  Save changes
                </button>
              </div>
            </div>
          </div>
        </class>
      </div>
    </div>

    <div class="card-body px-0 pt-0 pb-2">
      <div class="table-responsive p-0">
        <table class="table align-items-center mb-0">
          <thead>
            <tr>
              <th
                class="text-uppercase text-secondary text-xxs font-weight-bolder opacity-7"
              >
                Title
              </th>
              <th class="">Content</th>
              <th
                class="text-center text-uppercase text-secondary text-xxs font-weight-bolder opacity-7"
              >
                Edit
              </th>
              <th
                class="text-center text-uppercase text-secondary text-xxs font-weight-bolder opacity-7"
              >
                Delete
              </th>
              <th class="text-secondary opacity-7"></th>
            </tr>
          </thead>
          <div v-if="loading == true" style="padding-left: 100%">
            <LoadingBar />
          </div>
          <tbody v-else>
            <tr v-for="(item, index) in items" :key="index">
              <td style="white-space: normal">
                <div class="d-flex px-2 py-1">
                  <div>
                    <img
                      src="../../assets/img/team-2.jpg"
                      class="avatar avatar-sm me-3"
                      alt="user1"
                    />
                  </div>
                  <div class="">
                    <h6 class="mb-0 text-sm">{{ item.title }}</h6>
                    <!-- <p class="text-xs text-secondary mb-0">{{ item.content }}</p> -->
                  </div>
                </div>
              </td>
              <td style="width: 550px">
                <p
                  class="text-xs font-weight-bold mb-0"
                  style="white-space: normal; overflow: hidden"
                >
                  {{ item.content }}
                </p>
                <!-- <p class="text-xs text-secondary mb-0">{{ item.organization }}</p> -->
              </td>
              <td>
                <div class="ms-auto text-end">
                  <a
                    class="btn btn-link text-dark px-3 mb-0"
                    href="javascript:;"
                    data-toggle="modal"
                    data-target="#exampleModal"
                    @click="populateForm(item)"
                  >
                    <i
                      class="fas fa-pencil-alt text-dark me-2"
                      aria-hidden="true"
                    ></i
                    >Edit
                  </a>
                </div>
              </td>
              <td>
                <div class="ms-auto text-end">
                  <a
                    class="btn btn-link text-danger text-gradient px-3 mb-0"
                    href="javascript:;"
                  >
                    <i class="far fa-trash-alt me-2" aria-hidden="true"></i
                    >Delete
                  </a>
                </div>
              </td>
              <!----- <td class="align-middle text-center text-sm">
                <span class="badge badge-sm" :class="{'bg-gradient-success': item.status === 'Online', 'bg-gradient-secondary': item.status === 'Offline'}">{{ item.status }}</span>
              </td>
              <td class="align-middle text-center">
                <span class="text-secondary text-xs font-weight-bold">{{ item.employed }}</span>
              </td>
              <td class="align-middle">
                <a href="javascript:;" class="text-secondary font-weight-bold text-xs" data-toggle="tooltip" data-original-title="Edit user">Edit</a>
              </td> -->
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import LoadingBar from "../components/LoadingBar.vue";
import ArgonButton from "@/components/ArgonButton.vue";

export default {
  components: {
    ArgonButton,
    LoadingBar,
  },
  name: "authors-table",
  data() {
    return {
      formData: {
        imageFile: null,
        title: "",
        content: "",
      },
      
      items: [],
      image: null,
      loading: "",
      title: "",
      content: "",
      errorMessage: {
        title: "",
        content: "",
      },
    };
  },
  mounted() {
    // Fetch data from your API
    this.fetchData();
  },
  methods: {
    openModalAndFetchData() {
      // Call the openModal method to open the modal

      // Fetch data immediately after opening the modal
      // await this.fetchData();
      this.clearForm();
    },
    handleImageChange(event) {
      // Update image data when a file is selected
      this.image = event.target.files[0];
    },
    closeModal() {
      // Close the modal
      this.$refs.exampleModalRef.hide();
      // Fetch data and clear form
      this.fetchData();
      this.clearForm();
    },
    clearForm() {
      this.title = "";
      this.content = "";
      this.image = null;
      this.errorMessage.title = "";
      this.errorMessage.content = "";
    },
    populateForm(item) {
      this.title = item.title;
      this.content = item.content;
      // this.clearForm();
      // You may need additional logic to handle image data
      // For example, you could set this.image = item.logo_url;
    },
    async submitForm() {
      try {
        if (!this.title || !this.content) {
          this.errorMessage.title = "Title is required";
          this.errorMessage.content = "content is required";
          return;
          // throw new Error("Title and Content are required");
        }
        // Create a new FormData object
        const formData = new FormData();
        // Append form data
        formData.append("title", this.title);
        formData.append("content", this.content);
        formData.append("logo_url", this.image);

        // Send formData to the backend
        const response = await axios.post(
          "http://localhost:8000/api/homepages",
          formData,
          {
            headers: {
              "Content-Type": "multipart/form-data", // Set Content-Type header for FormData
            },
          }
        );

        console.log("API Response:", response.data);
        // Reset form fields
        this.title = "";
        this.content = "";
        this.image = null;
        this.errorMessage.title = "";
        this.errorMessage.content = "";

        this.fetchData();
      } catch (error) {
        console.error("API Error:", error);
        this.errorMessage =
          error.response.data.error ||
          "An error occurred while submitting the form";
      }
    },

    // async fetchData() {
    //   this.loading = true;
    //   try {

    //     const response = await axios.get("http://localhost:8000/api/homepages");
    //     this.items = response.data.data;
    //     this.clearForm();
    //     this.loading = false;
    //   } catch (error) {
    //     console.error("Error fetching data:", error);
    //   }
    // },
    async fetchData() {
      this.loading = true;
      try {
        await axios
          .get(`http://localhost:8000/api/homepages`)
          .then((result) => {
            this.items = result.data.data;
            setTimeout(() => {
              this.loading = false;
              this.clearForm();
            }, 1000);
          })
          .catch((err) => {
            console.log(err);
          });
      } catch (error) {
        console.error("Error fetching data:", error);
      }
    },
  },
};
</script>
